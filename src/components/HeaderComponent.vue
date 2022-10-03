<template>
  <header>
    <h2>Boolflix</h2>
    <div id="contenitore-bottone">
      <input
        type="text"
        v-model="inputText"
        @keyup.enter="$emit('ricerca', inputText)"
      />
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
    font-size: 0.8em;
  }
}
#contenitore-bottone {
  display: flex;
  margin-right: 10px;
  text-align: left;
  button {
    color: black;
  }
}
#contenitore-bottone input {
  margin-right: 10px;
}
</style>>

