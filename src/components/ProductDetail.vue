<template>
   <div class="product-detail">
      <p>{{ msg }}</p>
   </div>
</template>

<script>
   export default {
      name: 'ProductDetail',
      props: {
         msg: String,
         details: {
            type: String,
            required: false,
            default: '..'
         }
      },
      data() {
         return {   
         }
      },
      methods: {},
      computed: {}
   }
</script>