<template>
  <div id="app">
    <Top v-on:navigateTo="navigateTo" titol="Vue Shopping Cart" :cart="cart"/>
    <div v-if="page === 'products'" class="other">
      <ListProducts v-on:addItemToCart="addItemToCart"/>
    </div>
    <div v-if="page === 'cart'" class="compra">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
      <Back page="products" msg="Seguir comprant" v-on:navigateTo="navigateTo"></Back>
    </div>
  </div>
</template>

<script>
  import ListProducts from './components/ListProducts.vue'
  import Cart from './components/Carts.vue'
  import Top from './components/Top.vue'
  import Back from './components/Back.vue'
  export default {
    name: 'App',
    data: () => {
      return{
        cart:[],
        page:"products",
      };
    },
    components:{
      ListProducts,
      Cart,
      Top,
      Back
    },
    methods: {
      addItemToCart(product) {
        var trobat=false;
        var prod=JSON.parse(JSON.stringify(product["_props"]));
        for (var producto in this.cart) {
         if(this.cart[producto].name==prod.name){
          this.cart[producto].quantitat+=1;
          trobat=true;
         }
        }
        if(!trobat){
          prod.quantitat=1;
          this.cart.push(prod);
        }
      },
      removeItemFromCart(product) {
        this.comprat-=product.quantitat;
        this.cart.splice(this.cart.indexOf(product), 1);
      },
      navigateTo(page) {
        this.page = page;
      }
    } 
 }
</script>

<style>
  body{
    margin:0px;
    background: #d9dfe4f5;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  button:hover{
    background: black;
    color: white;
  }
</style>
