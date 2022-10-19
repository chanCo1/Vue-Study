<template>
  <div>
    <div>
      <!-- 체크박스의 v-model은 value와 관련있는게 아니고 -->
      <!-- checked와 관련 있다. -->
      <input
        type="checkbox"
        name=""
        id="html"
        value="HTML"
        v-model="favoriteLanguage"
      />
      <label for="html">HTML</label>
    </div>
    <div>
      <input
        type="checkbox"
        name=""
        id="css"
        value="CSS"
        v-model="favoriteLanguage"
      />
      <label for="css">CSS</label>
    </div>
    <div>
      <input
        type="checkbox"
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
      // 여러건을 선택할 수 있을 때는 배열로 ..
      favoriteLanguage: []
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {}
}
</script>
