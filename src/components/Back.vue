<template>
  <button class="continua" v-on:click="navigateTo(page)"><i class="fa fa-shopping-basket" aria-hidden="true">{{msg}}</i></button>
</template>

<script>
export default {
  name: 'Back',
  props: ["msg", "page"],
  methods: {
      navigateTo(page) {
        this.$emit("navigateTo", page);
      }
  }
}
</script>

<style scoped>
  .continua{
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
</style>