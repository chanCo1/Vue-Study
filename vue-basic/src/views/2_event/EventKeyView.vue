<template>
  <div>
    <!-- event를 사용할 때는 앞에 $를 붙여준다 -->
    <!-- <input type="search" @keyup="cheackEnter($event)" v-model="searchText"> -->
    <!-- keyup.enter 사용 -->
    <input type="search" @keyup.enter="doSearch" v-model="searchText">
    <button @click="doSearch">조회</button>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      searchText: ''
    }
  },
  setup() {},
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    doSearch() {
      console.log(this.searchText)
    },
    cheackEnter(event) {
      if (event.keyCode === 13) this.doSearch()
    }
  }
}
</script>
