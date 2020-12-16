<template>
  <div class="cart">
    <h2>La teva compra</h2>
    <table class="products">
      <tr class="titols">
          <th> Foto </th>
          <th> Nom </th>
          <th> Preu </th>
          <th> Quantitat </th>
          <th> Eliminar </th>
          <th> Total </th>
      </tr>
      <tr v-for="(product, index) in cart" :key="index">
        <th><img :src="product.image" style="height: 35px"/></th>
        <th>{{product.name}}</th>
        <th>{{product.price}}€</th>
        <th>{{product.quantitat}}
          <button v-on:click="reduirQuantitat(product)"><i class="fas fa-minus" style="font-size:20px; color:red"></i></button>
          <button v-on:click="product.quantitat += 1"><i class="fa fa-plus" style="font-size:20px; color:green"></i></button>
        </th>
        <th><button v-on:click="removeItemFromCart(product)"><i class="fa fa-trash-o" style="font-size:20px; color:red"></i></button></th>
        <th>{{(product.quantitat * product.price).toFixed(2)}} €</th>
      </tr>
      <tr>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
        <th> Total </th>
        <th> {{cart.reduce(function(acc, val) { return acc + (val.price*val.quantitat); }, 0).toFixed(2)}} € </th>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ["cart"],
  methods: {
    removeItemFromCart(product) {
      this.$emit("removeItemFromCart", product);
    },
    reduirQuantitat(product){
      product.quantitat-=1; 
      if(product.quantitat<1){
        this.removeItemFromCart(product);
      }
    }
  }
};
</script>

<style scoped>
  table{
    margin-left: auto;
    margin-right: auto;
    background-color: rgb(255, 255, 255);
    border-collapse: collapse;
    font-family: Arial, Helvetica, sans-serif;
    border-collapse: collapse;
    width: 50%;
  }

  table .titols{
    background-color: black;
    color: white;
  }

  tr{
    border: 1px solid #ddd;
  }

  th{
    border: 1px solid #ddd;
    width: 5%;
  }

  button{
    background-color: none;
  }

  i{
    background-color: none;
    background: none;
  }
  body{
    margin-bottom: 10%;
  }
</style>
