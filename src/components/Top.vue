<template>
    <header class="header">
      <button class="shop" v-on:click="navigateTo('cart')">
        <i class='fas fa-shopping-cart' style='font-size:30px'>{{cart.reduce(function(acc, val) { return acc + val.quantitat; }, 0)}}</i>
      </button>
      <h1> {{titol}}</h1>
    </header>
</template>

<script>
  export default {
    name: 'Top',
    props: ["cart", "titol"],
    methods: {
        navigateTo(page) {
          this.$emit("navigateTo", page);
        }
    }
  }
</script>

<style scoped>
  .header {
    position: relative;
    background: linear-gradient(to left, #300114, #86033a , #ac074c);
    background-size: cover;
    height: 15em;
  }
  h1 {
    position: absolute;
    text-align: center;
    top: 30%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 4em;
    text-shadow: 1px 3px 5px rgba(0,0,0,0.5), -1px -3px 5px rgba(0,0,0,0.5);
    font-family: 'Sofia', cursive;
  }

  .shop{
    cursor: pointer;
    float: right;
  }
</style>