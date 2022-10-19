<template>
  <div>
    <!-- v-model은 양방향 데이터 -->
    <input type="text" v-model="userId" />
    <!-- userId를 출력해보면 입력값이 나온다 -->
    <button @click="myFunction">클릭</button>
    <button @click="changeData">변경</button>

    <br />
    <br />

    <input type="text" v-model="num1" /> +
    <input type="text" v-model="num2" /> =
    <span>{{ num1 + num2 }}</span>

    <br />
    <br />

    <!-- v-model 뒤에 .number를 붙이면 parseInt와 같은 효과 -->
    <input type="text" v-model.number="num3" /> +
    <input type="text" v-model.number="num4" /> =
    <span>{{ num3 + num4 }}</span>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      userId: '이름을 입력하세요.',
      num1: 0,
      num2: 0,
      num3: 0,
      num4: 0
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    myFunction() {
      console.log(this.userId)
    },
    changeData() {
      this.userId = '쿄쿄쿄'
    }
  }
}
</script>
