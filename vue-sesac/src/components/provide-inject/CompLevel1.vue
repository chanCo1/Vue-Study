<!-- TODO: template -->
<template>
  <div>
    <h2>component1</h2>
    <CompLevel2 />
  </div>
</template>

<!-- TODO: script -->
<script>
import CompLevel2 from './CompLevel2.vue';

export default {
  name: 'CompLevel1',
  components: {
    CompLevel2
  },
  data() {
    return {
      userName: 'CHAN'
    };
  }
};
</script>

<!-- TODO: style -->
<style scoped></style>
