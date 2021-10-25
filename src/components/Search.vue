<template>
  <div class="m-5">
    <p>ユーザー検索</p>
    <input
      type="search"
      class="form-control"
      placeholder="ユーザー名"
      v-model="searchName"
    />
    <br />
    <button class="btn btn-info" v-on:click="doSearch">検索する</button>

  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchName: "",
    };
  },
  methods: {
    doSearch() {
      this.$emit("search-event", this.searchName);
    },
  },
};
</script>
