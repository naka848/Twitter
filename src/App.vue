// コンポーネントで出力される内容を扱う
<template>
  <div id="app">
    <Form
      title="ホーム"
      v-on:result-event="appAction" />
    <Search 
      v-on:search-event="searchAction"/>

    <!-- v-for="変数 in 配列"…配列の値を順に取り出して変数にいれ、タグを出力(p136) -->
    <!-- v-bind:属性名="設定する値"(p118) -->
    <!-- v-bind:key…v-forで配列からオブジェクトを取り出し処理する際に使うキーを指定 -->
    <!-- ①変数Tweetに配列AllTweetの値を取り出していれる
    ②属性名TweetObjに、変数Tweetの値を入れる
    ③変数Tweetの処理をするときに使うキーとしてtweet_idを指定 -->
    <Tweet
      v-for="Tweet in AllTweet"
      v-bind:TweetObj="Tweet"
      v-bind:key="Tweet.tweet_id"
    />
    <!-- <Filter
      v-for="Tweet in filteredTweet"
      v-bind:TweetObj="Tweet"
      v-bind:key="Tweet.tweet_id"
    /> -->
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Tweet from "./components/Tweet.vue";
// import Filter from "./components/Filter.vue";
import Search from './components/Search.vue';

export default {
  name: "App",
  components: {
    Form,
    Tweet,
    // Filter,
    Search,
  },

  // コンポーネントが読み込まれたときに動く部分
  // 定義、宣言をする
  data() {
    return {
      // Array.of()メソッド…配列を作成
      AllTweet: Array.of({
        tweet_id: 0,
        tweet_body: "はじめてのツイート",
        tweet_user: {
          user_id: "111",
          user_name: "first",
          // user_following:'',
          // user_followers:'',
        },
      }),
      filteredTweet:{
        tweet_id:'',
        tweet_body:'',
        tweet_user:{
          user_id:'',
          user_name:'',
        }
      }
    };
  },

  methods: {
    // receiveTweet（配列）…Formで入力された内容がはいってる
    appAction(receiveTweet) {
      // 配列AllTweetに対して、連想配列receiveTweetを追加する
      this.AllTweet.push(receiveTweet);
    },

    // 検索したユーザーのツイートだけを入れる配列filteredTweetを作成
    searchAction(searchName) {
      let i = 0;
      const filteredTweet = [];
      while (i < 10) {
        if (this.AllTweet[i].tweet_user.user_name === searchName) {
          // console.log(this.AllTweet[i]);
          filteredTweet.push(this.AllTweet[i]);
        }
        i++;
        console.log(filteredTweet);
      }
    },
  },
};
</script>


