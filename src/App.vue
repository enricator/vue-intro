<template>
    <div id="app">
        <div class="nav-bar">
            <div class="logo"><img alt="Vue logo" src="./assets/logo.png"></div>
            <div class="appname"><span> {{ appName}} </span></div>
            <div class="cart">
                <p>Cart({{ cart.length }})</p>
            </div>
        </div>


        <Product :premium="premium" @add-to-cart="addToCart" @remove-from-cart="removeFromCart" />

    </div>
</template>

<script>
    import Product from './components/Product.vue'

    export default {
        name: 'App',
        components: {
            Product
        },
        data() {
            return {
                premium: false,
                appName: 'Vue Products App',
                cart: []
            }
        },
        methods: {
            addToCart(id) {
                this.cart.push(id)
            },
            removeFromCart(id) {
                if (this.cart.indexOf(id) > -1) this.cart.splice(this.cart.indexOf(id), 1)
            }
        }
    }

</script>


<style lang="scss">
    $navbarH: 60px;

    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        // text-align: center;
        color: #2c3e50;
        //margin-top: 60px;
        margin-left: auto;
    }

    body {
        font-family: tahoma;
        color: #282828;
        margin: 0px;
    }

    .nav-bar {
        background: linear-gradient(-90deg, #84CF6A, #16C0B0);
        height: $navbarH;
        margin-bottom: 15px;

        .logo {
            height: $navbarH;
            float: left;


            img {
                margin: 2px 20px;
                height: 90%;
                width: auto;
                background: white;
            }

        }

        .appname {
            display: inline-block;
            height: $navbarH;

            span {
                margin: 20px;
                display: inline-block;
                color: white;
            }

        }
    }

    .product {
        display: flex;
    }

    img {
        border: 1px solid #d8d8d8;
        width: 70%;
        margin: 40px;
        box-shadow: 0px .5px 1px #d8d8d8;
    }

    .product-image {
        flex-basis: 700px;
    }

    .product-info {
        margin-top: 10px;
        flex-basis: 500px;
    }

    .color-box {
        width: 40px;
        height: 40px;
        margin-top: 5px;
    }

    .cart {
        margin-right: 25px;
        float: right;
        border: 1px solid #d8d8d8;
        border-radius: 10px;
        padding: 0px 20px;
        background-color: #fcfdab;
        margin-top: 2px;
        box-shadow: 6px 6px 12px 0px rgba(0, 0, 0, 0.28);
    }

    button {
        margin: 30px 10px;
        border: none;
        background-color: #1E95EA;
        color: white;
        height: 40px;
        padding: 0px 13px;
        font-size: 14px;
    }

    .disabledButton {
        background-color: #d8d8d8;
    }

    .review-form {
        width: 30%;
        padding: 20px;
        border: 1px solid #d8d8d8;
    }

    input {
        width: 100%;
        height: 25px;
        margin-bottom: 20px;
    }

    textarea {
        width: 100%;
        height: 60px;
    }

</style>
