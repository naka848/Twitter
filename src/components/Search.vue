<template>
  <div class="m-5">
    <p>ユーザー検索</p>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        name="selectUser"
        id="1"
        value="Aさん"
      />
      <label class="form-check-label" for="1">Aさん</label>
    </div>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        name="selectUser"
        id="2"
        value="Bさん"
      />
      <label class="form-check-label" for="2">Bさん</label>
    </div>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        name="selectUser"
        id="3"
        value="Cさん"
      />
      <label class="form-check-label" for="3">Cさん</label>
    </div>
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
      let userRadio = document.getElementsByName('selectUser');
      for (let i = 0; i < 3; i++) {
        if (userRadio.item(i).checked) {
          this.searchName = userRadio.item(i).value;
        }
      }
      this.$emit("search-event", this.searchName);
    },
  },
};
</script>
