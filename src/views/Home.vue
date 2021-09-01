<template>
  <div class="home">
    <h1>Browse Our Selection</h1>
    <div class="container">
      <ShopCart :item=item :key="item.id" v-for="item in items"/>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ShopCart from '@/components/ShopCart.vue'
import items from "../data/items.js"

export default {
  name: 'Home',
  data() {
    return {
      items: items
    }
  },
  components: {
    ShopCart,
  },
}
</script>

<style scoped>
.container {
    flex-wrap: wrap;
    display: flex;
    justify-content: center;
    margin: 0 auto;
}
</style>