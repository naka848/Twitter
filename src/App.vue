// コンポーネントで出力される内容を扱う
<template>
  <div id="app">
    <SelectUser v-on:selectUser-event="selectUser" />
    <Form title="Twitter" v-on:result-event="appAction" v-bind:user="tweet_user" />
    <Search v-on:search-event="searchAction" />

    <!-- ①変数Tweetに配列AllTweetの値を取り出していれる
    ②属性名TweetObjに、変数Tweetの値を入れる
    ③変数Tweetの処理をするときに使うキーとしてtweet_idを指定 -->
    <Tweet
      v-for="Tweet in AllTweet"
      v-bind:TweetObj="Tweet"
      v-bind:key="Tweet.tweet_id"
    />
  </div>
</template>

<script>
import SelectUser from "./components/SelectUser.vue";
import Form from "./components/Form.vue";
import Tweet from "./components/Tweet.vue";
import Search from "./components/Search.vue";

export default {
  name: "App",
  components: {
    SelectUser,
    Form,
    Tweet,
    Search,
  },

  data() {
    return {
      // Array.of()メソッド…配列を作成
      // 初回表示用のダミーデータ
      AllTweet: Array.of({
        tweet_id: 0,
        tweet_body: "はじめてのツイート",
        tweet_user: {
          user_id: "111",
          user_name: "first",
        },
      }),

      // 初回ロード時にForm.vueにpropsとして渡し、selectUser()で上書きするためのデータ
      tweet_user:{
        user_id: "5b",
        user_name: "nanashi",
      },
    };
  },

  methods: {
    selectUser(user) {
      this.tweet_user = user;
      // console.log(this.tweet_user);
    },

    // receiveTweet（配列）…Formで入力された内容がはいってる
    appAction(receiveTweet) {
      // 配列AllTweetに対して、連想配列receiveTweetを追加する
      this.AllTweet.push(receiveTweet);
    },

    // 検索したユーザーのツイートだけを入れる配列filteredTweetを作成
    searchAction(searchName) {
      let i = 0;
      const filteredTweet = [];
      while (i < this.AllTweet.length) {
        if (this.AllTweet[i].tweet_user.user_name === searchName) {
          filteredTweet.push(this.AllTweet[i]);
        }
        i++;
      }
      this.AllTweet = filteredTweet;
    },
  },
};
</script>


