<template>
    <div>
        <div v-for="cartPro in cart.products" v-bind:key="cartPro">
            <CartProduct :cartPro="cartPro" :products="findProduct(cartPro.productId)"> </CartProduct>
        </div>
    </div>  
</template>


<script>
import CartProduct from './CartProduct'

export default {
  components: { CartProduct },
  name: 'UserCartCard',
  props: {
    cart: Object,
    products:Array
  },
    methods:{
        findProduct(id){
            return this.products.find(item=>item.id === id)
        }
    },
}
</script>