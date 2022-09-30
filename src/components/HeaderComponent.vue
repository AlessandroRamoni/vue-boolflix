<template>
  <header>
    <h2>Boolflix</h2>
    <div id="contenitore-bottone">
      <input type="text" v-model="inputText" />
      <button @click="$emit('ricerca', inputText)">CERCA</button>
    </div>
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
  display: flex;
  justify-content: space-between;
  align-items: center;
  h2 {
    color: darkseagreen;
    text-align: left;
    padding: 20px;
    font-size: 1.3em;
  }
  input {
    background-color: darkseagreen;
    height: 25px;
  }
  button {
    background-color: darkseagreen;
    height: 25px;
    padding: 5px;
    color: #ffffff;
    cursor: pointer;
  }
}
#contenitore-bottone {
  display: flex;
}
#contenitore-bottone input {
  margin-right: 10px;
}
</style>>

