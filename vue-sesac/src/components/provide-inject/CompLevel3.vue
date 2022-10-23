<!-- TODO: template -->
<template>
  <div>
    <h2>component3</h2>
    <h3>Passed Data from App {{ name }}</h3>
  </div>
</template>

<!-- TODO: script -->
<script>
export default {
  name: 'CompLevel3',
  inject: ['name']
};
</script>

<!-- TODO: style -->
<style scoped></style>
