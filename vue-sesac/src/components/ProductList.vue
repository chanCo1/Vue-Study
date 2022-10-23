<template>
  <div>
    <ul>
      <ProductItem
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
    </ul>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
  name: 'ProductList',
  /**
   * @props products -> 제품 정보 / app.vue
   */
  props: {
    products: {
      type: Array,
      default: () => {
        return [];
      }
    }
  },
  components: {
    ProductItem
  }
};
</script>

<style></style>
