<template>
  <div>
    <!-- 직접 데이터 바인딩 할때는 v-bind -->
    <input type="text" v-bind:value="userId" readonly />
    <!-- :를 앞에 붙이면 v-bind는 생략 가능 -->
    <input type="text" :value="userId" readonly />

    <br />
    <br />

    <img :src="imgSrc" alt="" style="width: 100px; height: auto;">

    <br />
    <br />

    <input type="search" name="" id="" v-model="txt1">
    <button :disabled="txt1 === ''">조회</button>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      userId: 'chanCo',
      imgSrc: 'https://item.kakaocdn.net/do/493188dee481260d5c89790036be0e66effd194bae87d73dd00522794070855d',
      txt1: ''
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {}
}
</script>
