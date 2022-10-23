<!-- TODO: HTML-->
<template lang="">
  <div>
    <h2>Hello!! {{ userName }}</h2>
    <p>오늘은 {{ visitCount }}번째 방문</p>
    <p>{{ siteInfo.name }}</p>

    <!-- <ul>
      <li v-for="product in products" :key="product.id">{{ product }}</li>
    </ul> -->
  </div>
</template>

<!-- TODO: JS -->
<script>
export default {
  name: 'GreetingUser',
  props: {
    // userName: String
    userName: {
      type: String,
      default: 'UUSER!'
    },
    visitCount: {
      type: Number,
      default: 0
    },
    siteInfo: {
      type: Object,
      // 오브젝트나 배열인 경우 리턴해주는 함수 형태로 해줘야함
      default: () => {
        return {
          name: 'haha',
          teacher: 'you'
        };
      }
    }
  },
  methods: {},
  components: {},
  data() {
    return {};
  }
};
</script>

<!-- TODO: Style -->
<style scoped></style>
