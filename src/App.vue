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
      // localStorage.setItem(key, value); … keyとvalueをペアにしてデータを保存
      localStorage.setItem(
        JSON.stringify(receiveTweet.tweet_id),
        JSON.stringify(receiveTweet)
      );
    },

    created(){
      for (let i = 1; i < localStorage.length; i++){
        // JSON.parse() … 文字列を JSON として解析し、文字列によって記述されている JavaScript の値やオブジェクトを構築する
        // localStorage.getItem(key); … keyに対応するvalueを取得
        this.AllTweet.push(JSON.parse(localStorage.getItem(i)));
      }
    },

    // 検索したユーザーのツイートだけを入れる配列filteredTweetを作成
    // searchAction(searchName) {
    //   let i = 0;
    //   const filteredTweet = [];
    //   while (i < this.AllTweet.length) {
    //     if (this.AllTweet[i].tweet_user.user_name === searchName) {
    //       filteredTweet.push(this.AllTweet[i]);
    //     }
    //     // console.log(searchName);
    //     // console.log(JSON.parse(localStorage.getItem(1)).tweet_user.user_name);
    //     i++;
    //   }
    //   this.AllTweet = filteredTweet;
    // },

    // ２回目の検索ができないので、できるようにしたい
    // ローカルストレージから検索結果をひっぱってくるようにしようとしてエラー
    searchAction(searchName) {
      let i = 0;
      const filteredTweet = [];
      while (i < this.AllTweet.length) {
        if ((JSON.parse(localStorage.getItem(i)).tweet_user.user_name) === searchName) {
          filteredTweet.push(this.localStorage.getItem(i));
        }
        i++;
      }
      this.AllTweet = filteredTweet;
    },


  },
};


// 11/30 一旦作業終了
// ローカルリポジトリへの理解がすこしできた
// ユーザー検索は途中でバグってとまってる
// localStorage.lengthの長さが取得できないバグがあるらしいので、そのせいか？



</script>





