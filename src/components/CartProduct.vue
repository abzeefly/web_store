<template>
    <div>
        <b-card>
            <b-img :height="40" :width="30" :src="products.image"></b-img>
             <p><strong>{{products.title}}</strong></p>
             <p> QTY: {{cartPro.quantity}} </p>
        </b-card>
    </div>
</template>

<script>
export default {
  name: 'CartProduct',
  props: {
    cartPro: Object,
    products: Object
  }
}
</script>