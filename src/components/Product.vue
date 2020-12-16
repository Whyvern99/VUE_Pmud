<template>
    <div class="card">
        <div class="image">
            <img :src="image" style="width:150px">
        </div>
        <div class="container">
            <h4><b>{{name}}</b></h4>
            <p>Preu: {{price}} €</p>
            <button v-on:click="addItemToCart()"> add to cart </button>
        </div>
    </div> 
</template>

<script>
export default {
  name: 'Product',
  props: {
    name: String,
    price: Number,
    image: String,
  },
  methods: {
    addItemToCart(){
      this.$emit("addItemToCart", this);
    }
  }
}
</script>

<style scoped>
    .card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        padding-bottom: 30px;
        transition: 0.3s;
    }
    .image{
        height: 170px;
    }
    img{
        display: inline-block;
        vertical-align: middle;
    }
    button{
        appearance: none;
        padding: 0.5em;
        margin: 0.5em 0;
        background: white;
        border: 1px solid black;
        transition: all 0.1s;
        font-size: 14px;
        cursor: pointer;
        user-select: none;
    }
    button:hover{
        background: black;
        color: white;
    }
    button:active {
        background-color: #3e8e41;
        transform: translateY(4px);
    }
</style>