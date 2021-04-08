<template>
    <div>
      <b-navbar type="dark" variant="dark">
         <b-navbar-brand href="#" v-b-toggle.sidebar-edit>
          <b-img left src="https://picsum.photos/50/50/?image=58"  class="d-inline-block align-top" alt="profile photo" rounded="circle"></b-img>
        </b-navbar-brand>
        <UserInfoEditBar :user ="user"> </UserInfoEditBar>
        <b-nav-form class="mx-auto">
          <b-form-input size="md" style="width:100%" v-model="searchString" class="searchBar" placeholder="Search"></b-form-input>
        </b-nav-form>
        <div class="options">
          <b-col>
            <b-row>
              <b-navbar-nav>
                <b-form-checkbox
                v-model="sortByPrice"
                :value="true"
                size="sm"
                :unchecked-value="false"
                button
                class="sortOption">
                Sort By Price
                </b-form-checkbox>
              </b-navbar-nav>
            </b-row>
            <b-row>
              <b-navbar-nav>
                  <b-nav-item-dropdown text="Categories" right>
                      <b-form-checkbox-group 
                        v-model="selectedCategories"
                        :options="categories"
                        stacked
                        >
                      </b-form-checkbox-group>
                  </b-nav-item-dropdown>
              </b-navbar-nav>
            </b-row>
          </b-col>
        </div>
        <b-navbar-nav>
          <b-nav-item id="popover-button-variant" href="#"> <b-icon icon="cart-4" font-scale="2.5"></b-icon></b-nav-item>
        </b-navbar-nav>
      </b-navbar>
      <b-popover target="popover-button-variant" triggers="focus">
        <UserCartCard :products="products" :cart="cart"> </UserCartCard>
      </b-popover>
    </div>
</template>

<script>
import UserCartCard from './UserCartCard'
import UserInfoEditBar from './UserInfoEditBar'

export default {
  components: { UserInfoEditBar, UserCartCard },
  name: 'ProductSearchBar',
  props: {
    user: Object,
    cart: Object,
    categories : Array,
    products:Array
  },
  data(){
    return{
      selectedCategories:[],
      searchString: null,
      sortByPrice:false
    }
  },
  methods:{
    
  }

}
</script>

<style scoped>
.sortOption{
  color:lightgrey;
}

</style>