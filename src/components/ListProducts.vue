<template>
  <div>
    <div v-for="(product, index) in products" :key="index" class="cart">
       <Product :name="product.name" :price="product.price" :image="product.image"
       v-on:addItemToCart="addItemToCart" />
    </div>
  </div>
</template>

<script>
  import Product from './Product.vue'
  export default {
    data: () => {
      return {
        products: [
          {
            name:"Poma",
            price:1.50, 
            image:"https://i.pinimg.com/originals/63/64/fb/6364fbeede3157aac881ed9c088d9c26.png"
          },
          {
            name:"Pera",
            price:1.20,
            image:"https://i.pinimg.com/474x/1a/86/c8/1a86c8c2a2dc5ba0a06a633cf6aa07df.jpg"
          },
          {
          name:"Taronja",
          price:0.85,
          image:"https://st.depositphotos.com/1000141/1963/i/600/depositphotos_19638723-stock-photo-fresh-orange-fruit-with-leaf.jpg" 
          },
          {
          name:"Llimona",
          price:0.95,
          image:"https://cdn.shopify.com/s/files/1/0064/2714/8335/products/limon-eco.jpg?v=1551190376" 
          }
        ]
      };
    },
    components:{
      Product
    },
    methods: {
      addItemToCart(product){
        this.$emit("addItemToCart", product);
      }
    }
  }
</script>

<style scoped>
    .container {
        padding: 2px 16px;
    }
    .cart{
        display: inline-block;
        margin: 2%;
        width: 200px;
        height: auto;
        background-color: white;
    }
</style>