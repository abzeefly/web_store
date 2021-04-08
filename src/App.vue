<template>
    <div id="app">
        <ProductSearchBar :products="products" ref="productbar" :user="user" :cart="cart" :categories="categories"></ProductSearchBar>
        <div v-if="selected.length==0 && search.length==0" >
            <b-card-group deck>
                <div v-for="product in products" v-bind:key="product.productId">
                    <ProductCard :product="product"></ProductCard>
                </div>
            </b-card-group>
        </div>
        <div v-else-if="selected.length > 0 &&  search.length==0">
            <b-card-group deck>
                <div v-for="product in products" v-bind:key="product.productId">
                    <div v-if="selected.indexOf(product.category) > -1">
                        <ProductCard :product="product"></ProductCard>
                    </div>
                </div>
            </b-card-group>
        </div>
        <div v-else-if="search.length > 0 && selected.length==0">
            <b-card-group deck>
                <div v-for="product in products" v-bind:key="product.productId">
                    <div v-if="product.title.toLowerCase().includes(search.toLowerCase())">
                        <ProductCard :product="product"></ProductCard>
                    </div>
                </div>
            </b-card-group>
        </div>
        <div v-else>
            <b-card-group deck>
                <div v-for="product in products" v-bind:key="product.productId">
                    <div v-if="product.title.toLowerCase().includes(search.toLowerCase()) && selected.indexOf(product.category) > -1">
                        <ProductCard :product="product"></ProductCard>
                    </div>
                </div>
            </b-card-group>
        </div>
    </div>
</template>

<script>
import ProductSearchBar from './components/ProductSearchBar'
import ProductCard from './components/ProductCard'
import _ from 'lodash';

export default {
  name: 'App',
  components: {
    ProductSearchBar,
    ProductCard
  },
  data() {
    return {
      products : [],
      user : null,
      cart : null,
      categories: null,
      search:'',
      selected : [],
      sortBy : false,
      productList:[],


    }
  },
  async created(){
    var response = await fetch('https://fakestoreapi.com/products')
    this.productList = await response.json()
    this.products = this.productList

    response = await fetch('https://fakestoreapi.com//users/1')
    this.user = await response.json()
    this.user.info = {}
    this.user.info.fullname = this.capitalise(this.user.name.firstname) + ' ' + this.capitalise(this.user.name.lastname)
    this.user.info.email = this.user.email
    this.user.info.username = this.user.username
    this.user.info.password = this.user.password
    this.user.info.address = `${this.user.address.number}, ${this.capitalise(this.user.address.street)} ${this.capitalise(this.user.address.city)}, ${this.user.address.zipcode}`

    response = await fetch('https://fakestoreapi.com/carts/1')
    this.cart = await response.json()

    response = await fetch('https://fakestoreapi.com/products/categories')
    this.categories = await response.json()

    console.log(this.products,this.user.info, this.cart, this.categories)
    
  },
  methods:{
      capitalise(s){
          return s.charAt(0).toUpperCase() + s.slice(1)
    },

  },
  mounted(){
    this.$watch(
      "$refs.productbar.selectedCategories",
      (new_value) => {
         this.selected = new_value
         console.log(this.selected)
        }
    )
    this.$watch(
        "$refs.productbar.searchString",
        (new_value) => {
            this.search = new_value
            console.log(this.search)
        }
    )
    this.$watch(
        "$refs.productbar.sortByPrice",
        (new_value)=>{
            this.sortBy = new_value
            console.log(this.sortBy)
            if(new_value){
                this.products = this.orderedProducts
            }else{
                this.products = this.productList
            }

        }
    )
  },
  computed:{
      orderedProducts :function(){
          return _.orderBy(this.products, 'price')
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}

</style>
