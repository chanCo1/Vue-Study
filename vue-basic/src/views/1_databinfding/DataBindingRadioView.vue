<template>
  <div>
    <div>
      <input
        type="radio"
        name=""
        id="html"
        value="HTML"
        v-model="favoriteLanguage"
      />
      <label for="html">HTML</label>
    </div>
    <div>
      <input
        type="radio"
        name=""
        id="css"
        value="CSS"
        v-model="favoriteLanguage"
      />
      <label for="css">CSS</label>
    </div>
    <div>
      <input
        type="radio"
        name=""
        id="js"
        value="JS"
        v-model="favoriteLanguage"
      />
      <label for="js">JavaScript</label>
    </div>

    <div>선택한 지역: {{ favoriteLanguage }}</div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      // 하나만 선택할 수 있을 때는 문자열로
      favoriteLanguage: ''
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {}
}
</script>
