<template>
  <div id="shop" class="product">
    <div class="product-image">
      <img :src="image" />
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
      <div v-for="v in variants" :key="v.id">
        <p>{{ v.color }}</p>
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
            {id: 2234, color:'green'},{id:2235, color:'blue'}
        ]
    }}
}
</script>

<style scoped>
h1 {
  color: red;
}
#shop {
  text-align: left;
}
</style>
