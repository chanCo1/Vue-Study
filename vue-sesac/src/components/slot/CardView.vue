<template>
  <div class="card">
    <!-- <slot>Default Value</slot> -->
    <div class="card-header">
      <slot name="header"></slot>
    </div>
    <div class="card-body">
      <slot name="body"></slot>
    </div>
    <div class="card-footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  padding: 1rem;
  margin-bottom: 1rem;
  width: 200px;
}

.card .card-header {
  color: red;
}
.card .card-body {
  color: green;
}
.card .card-footer {
  color: pink;
}
</style>
