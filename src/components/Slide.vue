<template>
  <div :class="[show ? 'show' : '', 'slide']" />
    <div :class="[show ? 'show' : '', 'drawer']">
      <div class="product-details">
        <h3>
        {{ item.title }} 
        <i @click="removeSlide" class="fas fa-times"></i>
        </h3>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Debitis
            provident, earum qui ipsa tenetur numquam, dolorem fuga rem doloribus
            quas officiis eligendi possimus! Cupiditate dolor recusandae, unde
            delectus hic doloribus! Lorem ipsum dolor sit amet consectetur
            adipisicing elit. Culpa et pariatur fugiat, repellendus distinctio
            accusamus molestiae omnis quia in esse inventore voluptas maxime, unde
            dolor obcaecati delectus eligendi exercitationem. Ipsam?
        </p>
        <p>Price: {{ item.price }}</p>
        <div v-if="product_total">
          <p>In Cart</p>
          <p>{{ product_total }}</p>
        </div>
        <div class="button-container">
          <button @click="removeFromCart()">Remove</button>
          <button @click="addToCart()">Add</button>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    name: 'Slide',
    props: {
        item: Object,
        show: Boolean
    },
    methods: {
        removeSlide() {
            this.$emit('remove-slide')
        },
        addToCart() {
          this.$store.commit('addToCart', this.item)
        },
        removeFromCart() {
          this.$store.commit('removeFromCart', this.item)
        }
    },
    computed: {
      product_total() {
        return this.$store.getters.productQuantity(this.item)
      }
    }
}
</script>

<style lang="scss" scoped>
.slide {
  height: 100vh;
  width: 100%;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 2;
  background-color: rgba(124, 124, 124, 0.55);
  display: none;
  transition: display 5s;
  &.show {
    display: block;
  }
}
.drawer {
  width: 95%;
  height: 100vh;
  overflow-y: scroll;
  background-color: white;
  position: fixed;
  z-index: 4;
  top: 0;
  left: -105vw;
  padding: 15px;
  transition: 0.5s linear;
  &.show {
    left: 0;
  }
}
i {
  float: right;
  width: 15px;
  padding: 5px;
  font-size: 1.5rem;
  border: 2px solid grey;
  color: grey;
  border-radius: 5px;
  right: 10px;
  cursor: pointer;

  &.hover {
    background-color: lightgrey;
  }
}
.product-details {
  display: flex;
  justify-content: center;
  flex-direction: column;

  h3 {
    margin-bottom: 50px
  }
  h3 + p {
    line-height: 1.5rem;
    padding: 20px;
  }

  button {
    margin: 0 5px 50px 5px;
    border: none;
    width: 150px;
    padding: 10px;
    border-radius: 5px;
    cursor: pointer;
  }
}
@media (min-width: 500px) {
  .drawer {
      width: 450px;
  }
}
</style>