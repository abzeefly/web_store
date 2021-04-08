<template>
    <div class="product">
        <b-card class="productCard">
            <b-row no-gutters>
                <b-col sm="4" md="4" lg="1">
                    <b-card-img class="productImage my-auto" fluid center :src="product.image">
                    </b-card-img>
                </b-col>
                <b-col class="cardContent" sm="8" md="6" lg="8">
                    <b-card-body :title="product.title">
                        <b-card-sub-title class="mb-2">${{product.price}}</b-card-sub-title>
                        <b-card-text>
                            {{product.description}}
                        </b-card-text>
                        <b-card-sub-title><strong>{{product.category.toUpperCase()}}</strong></b-card-sub-title>
                        <!-- <b-card-text> 
                            <b-button href="#" variant="primary">Add to Cart  <b-icon icon="cart-plus"></b-icon></b-button>
                        </b-card-text> -->
                    </b-card-body>
                </b-col>
            </b-row>
        </b-card>    
    </div>

</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: Object,
  }
}

</script>

<style scoped>
.productCard{
    margin : 10px;
    padding : 10px;
}
.productImage{
    min-width: 150px;
    margin:10px;
    
}
.cardContent{
    left:10%

}
.product{
    margin-left:8%;
    margin-right: 8% ;
}
</style>