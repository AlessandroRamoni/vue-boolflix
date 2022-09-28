<template>
  <header>
    <h2>Boolflix</h2>
    <!-- <input type="text" v-model="searchText" @keyup.enter="doSearch()" /> -->
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
};
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(2, 16, 80);
  h2 {
    color: darkseagreen;
    text-align: left;
    padding: 20px;
    font-size: 1.3em;
  }
}
</style>>

