<template lang="">
  <div>
    <li>
      <p class="title">{{ product.name }}</p>
      <img
        :src="`https://placeimg.com/200/100/${product.id}`"
        alt="product.name"
        class="image"
      />
      <p class="price">{{ product.price }}</p>
    </li>
  </div>
</template>
<script>
export default {
  name: 'ProductItem',
  /**
   * @props products 제품정보 / ProductList.vue
   */
  props: {
    product: Object
  }
};
</script>
<style scoped>
li {
  border: 2px solid salmon;
  margin: 10px 0;
}
.title {
  font-size: 24px;
  color: #2c82c9;
  font-weight: bold;
}
</style>
