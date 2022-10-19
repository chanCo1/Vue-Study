<template>
  <div>
    <div style="color: red; font-size: 30px;">
      스타일 바인딩: 컬러는 red, 글씨크기는 30px
    </div>
    <div :style="style1">
      스타일 바인딩: 컬러는 green, 글씨크기는 50px
    </div>

    <button @click="style1.color='blue'">색상바꾸기</button>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      style1: {
        color: 'green',
        fontSize: '50px'
      }
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {}
}
</script>
