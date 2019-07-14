<template>
  <div id="shop">
    <h1>{{ product }}</h1>
  </div>
</template>

<script lang="js">
export default {
    data : function () {return {product: 'Socks'}}
}
</script>

<style lang="scss">
#shop {
  color: red;
}
</style>
