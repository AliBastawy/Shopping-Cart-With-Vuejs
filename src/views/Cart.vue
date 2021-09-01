<template>
  <div class="about">
    <h1>Your Cart</h1>
    <div
      v-for="item in cartItems"
      :key="item.id"
      class="cart"
    >
      <div class="head">
        <p>{{ item.title }}</p>
        <p>In Cart: {{ item.order }}</p>
        <p>
          Total Cost: ${{ item.price * item.order }}.00
        </p>
      </div>
      <div>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Non velit quis
        quisquam nesciunt, debitis sit quod ducimus consequuntur fugit
        voluptatum vitae? Voluptatibus sapiente labore quisquam rerum dolores
        modi provident eius.
      </div>
    </div>
    <div class="total cart">
      <p>Cart Total: ${{ cart_Total }}.00</p>
      <button>Pay by Credit Card</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  data() {
    return {
      totalPrice: 0,
    };
  },
  computed: {
    cart_Total() {
      return this.$store.getters.cartTotal
    },
    cartItems() {
      return this.$store.getters.cartItems
    },
  },
};
</script>

<style scoped>
.cart {
  background-color: #fff;
  padding: 10px;
  border-radius: 7px;
  margin: 20px 15px;
}
.head {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
  font-size: 20px;
}
button {
  color: white;
  background-color: #2180f7;
  padding: 9px 14px;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  display: block;
  margin-top: 15px;
}
.total {
  text-align: left;
  padding: 20px 15px;
  font-weight: 700;
  font-size: 19px;
}
</style>
