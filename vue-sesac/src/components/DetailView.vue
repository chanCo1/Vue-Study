<!-- TODO: template -->
<template>
  <div class="wrapper">
    <div class="container">
      <h2>Detailpage</h2>
      <button @click="closeDetail">close</button>
      <input type="text" v-model="userName" />
      <button @click="sendData">데이터 보내기</button>
    </div>
  </div>
</template>

<!-- TODO: script -->
<script>
export default {
  name: 'DetailView',
  data() {
    return {
      userName: ''
    };
  },
  /**
   * @props displayDetail - 모달창 on/off / App.vue
   */
  props: {
    displayDetail: Boolean
  },
  methods: {
    closeDetail() {
      this.$emit('closeDetail');
    },
    sendData() {
      this.$emit('sendData', this.userName);
    }
  }
};
</script>

<!-- TODO: style -->
<style scoped>
.wrapper {
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  width: 300px;
  height: 300px;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background-color: #fff;
  width: 60%;
}
</style>
