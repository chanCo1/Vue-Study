<!-- TODO: HTML-->
<template lang="">
  <div>
    <h2>Hello!! {{ userName }}</h2>
    <p>오늘은 {{ visitCount }}번째 방문</p>
    <p>{{ siteInfo.name }}</p>
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
    return {
      products: [
        { name: 'TV', price: 500000, company: 'LG' },
        { name: '전자레인지', price: 200000, company: '삼성' },
        { name: '가스오븐', price: 300000, company: '한화' },
        { name: '냉장고', price: 50000, company: '대우' },
        { name: '에어컨', price: 100000, company: '해태' }
      ]
    };
  }
};
</script>

<!-- TODO: Style -->
<style scoped></style>
