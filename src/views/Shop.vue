<template>
  <div id="shop" class="product">
    <div class="product-image">
      <img :src="image" />
      <figcaption>
        <span
          id="cursorDefault"
          v-for="v in variants"
          :key="v.id"
          @mouseover="updateProduct(v.image)"
          :style="getColor(v.color)"
        >
          {{ v.color }}
        </span>
      </figcaption>
    </div>
    <div class="product-info">
      <h1>{{ product }}</h1>
      <p>{{ desc }}</p>
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <ul>
        <!--eslint-disable-next-line-->
        <li v-for="detail in details">{{ detail }}</li>
      </ul>
      <button @click="updateCart(1)">Add to Cart</button>
      <button id="b2" @click="updateCart(-1)">Remove from Cart</button>
      <div class="cart">
        <p>Cart({{ cart }})</p>
      </div>
    </div>
  </div>
</template>

<script lang="js">
export default {
    data : function () {return {
        product: 'Socks',
        desc: 'A pair of warm, fuzzy socks',
        image: require('../assets/socks.jpg'),
        inStock: true,
        details: ['80% cotton', '20% polyester', 'gender-neutral'],
        variants: [
            {
                id: 2234,
                color: 'green',
                image: require('../assets/socks.jpg')
            },
            {
                id:2235,
                color:'blue',
                image: require('../assets/bluesock.jpg')
            }
        ],
        cart: 0
    }},
    methods : {
        updateCart(val) {
            if (val == -1 && this.cart == 0) {
                val = 0;
            }
            this.cart += val
        },
        updateProduct(img) {
            this.image = img
        },
        getColor(color) {
            return { border: '1px solid ' + color }
        }
    }
}
</script>

<style scoped>
button {
  cursor: pointer;
}
h1 {
  color: red;
}
figcaption {
  text-align: center;
}
#shop {
  text-align: left;
}
#b2 {
  margin-left: 5%;
}
#cursorDefault {
  cursor: default;
}
</style>
