<template>

   <div class="product">

      <div class="product-image">
         <img :src="image" />
      </div>

      <div class="product-info">
         <h1>{{ product }}</h1>
         <p v-if="inStock">In Stock</p>
         <p v-else>Out of Stock</p>

         <p>Shipping: {{ shipping }}</p>

         <ul>
            <li v-for="(detail, index) in details" :key="index">{{ detail }}</li>
         </ul>


         <div class="color-box" v-for="(variant, index) in variants" :key="variant.variantId" :style="{ backgroundColor: variant.variantColor }" @mouseover="updateProduct(index)">
         </div>

         <button v-on:click="addToCart" :disabled="!inStock" :class="{ disabledButton: !inStock }">
            Add to cart
         </button>

         <button v-on:click="removeFromCart" :disabled="!inStock" :class="{ disabledButton: !inStock }">
            Remove from cart
         </button>
         
         <!-- <DummyButton /> -->

      </div>

   </div>

</template>

<script>
   // import ProductDetail from './components/ProductDetail.vue'
   // import DummyButton from 'DummyButton.vue'

   export default {
      name: 'Product',
      components: {
         //DummyButton
      },
      props: {
         msg: String,
         premium: {
            type: Boolean,
            required: true
         }
      },
      data() {
         return {
            product: 'Socks',
            brand: 'Vue Mastery',
            selectedVariant: 0,
            details: ['80% cotton', '20% polyester', 'Gender-neutral'],
            variants: [{
                  variantId: 2234,
                  variantColor: 'green',
                  variantImage: './img/vmSocks-green-onWhite.jpg',
                  variantQuantity: 10
               },
               {
                  variantId: 2235,
                  variantColor: 'blue',
                  variantImage: './img/vmSocks-blue-onWhite.jpg',
                  variantQuantity: 0
               }
            ]
         }
      },
      methods: {
         addToCart() {
            //this.cart += 1
            this.$emit('add-to-cart', this.variants[this.selectedVariant].variantId)
         },
         removeFromCart() {
            //this.cart += 1
            this.$emit('remove-from-cart', this.variants[this.selectedVariant].variantId)
         },
         updateProduct: function(index) {
            this.selectedVariant = index
            //console.log(index)
         }
      },
      computed: {
         title() {
            return this.brand + ' ' + this.product
         },
         image() {
            return this.variants[this.selectedVariant].variantImage
         },
         inStock() {
            return this.variants[this.selectedVariant].variantQuantity
         },
         shipping() {
            if (this.premium) {
               return "Free"
            }
            return 2.99
         }


      }
   }

</script>
