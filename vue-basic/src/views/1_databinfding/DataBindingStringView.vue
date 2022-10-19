<template>
  <!-- html 태그는 template 안에 -->
  <div> <!-- 에러는 아니지만, 감싸줘야 한다. <></>같은 느낌 -->
    <h1>Hello {{ userName }}!</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script>
// 자바스크립트 코드는 여기에
export default {
  data() {
    return {
      userName: 'chanCo',
      message: 'Welcome ~~'
    }
  }
}
</script>

<!-- scoped가 있으면 작성된 환경에만 적용됨 -->
<style scoped>
/* css는 여기에 */
</style>
