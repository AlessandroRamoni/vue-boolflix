<template>
  <header>
    <h2>Boolflix</h2>
    <input type="text" v-model="inputText" />
    <button @click="$emit('ricerca', inputText)">CERCA</button>
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      inputText: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(2, 16, 80);
  position: relative;
  h2 {
    color: darkseagreen;
    text-align: left;
    padding: 20px;
    font-size: 1.3em;
  }
}
input {
  background-color: darkseagreen;
  position: absolute;
  right: 10px;
  top: 20px;
}
</style>>

