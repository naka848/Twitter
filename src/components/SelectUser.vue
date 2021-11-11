<template>
  <div class="menu m-5">
    <p>ユーザーの切り替え</p>
    <!-- <select>タグ…ユーザーにプルダウン形式で入力値を選択してもらう時に使用するタグ -->
    <!-- 選択された入力値をselectedUserとする -->
    <select class="form-select" v-model="selectedUser">
      <option
        v-for="tweet_user in tweet_users"
        v-bind:value="tweet_user"
        v-bind:key="tweet_user.user_id"
      >
        {{ tweet_user.user_name }}
      </option>
    </select>
    <br />
    <button class="btn btn-info" v-on:click="changeUser">変更する</button>
  </div>
</template>

<script>
export default {
  name: "SelectUser",
  data() {
    return {
      tweet_users: [
        { user_id: "test_a", user_name: "Aさん" },
        { user_id: "test_b", user_name: "Bさん" },
        { user_id: "test_c", user_name: "Cさん" },
      ],
      selectedUser: {
        user_id: "test_a",
        user_name: "Aさん",
      },
    };
  },

  updated: function () {
    console.log(this.data.TweetObj.tweet_user);
  },
  methods: {
    changeUser() {
      this.$emit("selectUser-event", this.selectedUser);
    },
  },
};
</script>