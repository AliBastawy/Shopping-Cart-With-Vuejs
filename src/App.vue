<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/cart">Cart</router-link>
  </div>
  <router-view/>
</template>

<script>
export default {
  mounted() {
    this.$store.commit('updateCartFromLocalStorage')
  },
}
</script>

<style lang="scss">
body {
  background-color: rgb(245,245,245);
  overflow-x: hidden;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 20px;
  line-height: 30px;
  height: 30px;
  background-color: #fff;

  a {
    font-weight: bold;
    color: darkgrey;
    margin: 0 5px 0 5px;
    font-size: 1.25rem;
    text-decoration: none;

    &.router-link-exact-active {
      color: #2c3e50;
    }
  }
}
</style>
