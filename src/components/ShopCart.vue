<template>
    <div class="cart">
        <h3>{{ item.title }}</h3>
        <h5>Price: ${{ item.price.toFixed(2) }}</h5>
        <p>
            Description: Lorem ipsum dolor sit amet consectetur adipisicing
            elit. Sint aliquam officiis saepe, ipsa nemo laboriosam illo
            laborum quas ex pariatur
        </p>
        <p>{{ item.itemDes }}</p>
        <button @click="onClick(item)">View Product</button>
    </div>
    <Slide
        :show="show"
        @remove-slide="removeSlide"
        :item=item
    />
</template>

<script>
import Slide from "./Slide";

export default {
    name: "ShopCart",
    props: {
        item: Object
    },
    components: {
        Slide,
    },
    data() {
        return {
            itemObj: [{}],
            show: false,
        };
    },
    methods: {
        onClick(item) {
            this.show = true;
            this.itemObj = item;
        },
        removeSlide() {
            this.show = false;
        },
        // async increaseOrder(id) {
        //     const getItem = await this.fetchItem(id);
        //     let updateOrder = getItem.order;
        //     updateOrder++;
        //     const updItem = { ...getItem, order: updateOrder, showCart: true };
        //     const res = await fetch(`api/items/${id}`, {
        //         method: "PUT",
        //         headers: {
        //             "Content-type": "application/json",
        //         },
        //         body: JSON.stringify(updItem),
        //     });
        //     const data = await res.json();
        //     this.items.filter((item) =>
        //         item.id === id ? (item.order = data.order) : "",
        //     );
        // },
        // async decreaseOrder(id) {
        //     const getItem = await this.fetchItem(id);
        //     let updateOrder = getItem.order;
        //     updateOrder--;
        //     let updateShow = true;
        //     if (updateOrder <= 0) {
        //       updateOrder = 0
        //       updateShow = false
        //     }
        //     const updItem = { ...getItem, order: updateOrder, showCart: updateShow };
        //     const res = await fetch(`api/items/${id}`, {
        //         method: "PUT",
        //         headers: {
        //             "Content-type": "application/json",
        //         },
        //         body: JSON.stringify(updItem),
        //     });
        //     const data = await res.json();
        //     this.items.filter((item) =>
        //         item.id === id ? (item.order = data.order) : "",
        //     );
        // },
        // async fetchItems() {
        //     const res = await fetch("api/items");
        //     const data = await res.json();
        //     return data;
        // },
        // async fetchItem(id) {
        //     const res = await fetch(`api/items/${id}`);
        //     const data = await res.json();
        //     return data;
        // },
    },
    // async created() {
    //     this.items = await this.fetchItems();
    // },
};
</script>
<style lang="scss" scoped>
.cart {
    background-color: #fff;
    margin: 10%;
    width: 80%;
    padding: 10px;
    box-shadow: 0 0 5px grey;
    border-radius: 5px;
    
    h5 {
        color: grey;
    }
    h5 + p {
        font-size: 0.85rem;
    }
    p:last-of-type() {
        color: grey
    }
}
button {
    padding: 10px;
    border-radius: 5px;
    border: none;
    cursor: pointer;
    font-weight: bold;
    font-size: 1.15rem;
}
.cart button {
    color: white;
    background-color: rgb(79, 160, 187);
}
@media (min-width: 500px) {
    .cart {
        width: 350px;
        margin: 10px;
    }
}
</style>
