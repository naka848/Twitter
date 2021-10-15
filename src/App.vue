// コンポーネントで出力される内容を扱う
<template>
  <div id="app">
    <Form
      title="ホーム"
      v-on:result-event="appAction"
      v-on:search-event="searchAction"
    />

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

    <hr />
    <p>検索結果を表示</p>
    <!-- <Filter 
    v-bind:obj="AllTweet" /> -->
    <Filter
      v-for="Tweet in filteredTweet"
      v-bind:TweetObj="Tweet"
      v-bind:key="Tweet.tweet_id"
    />
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Tweet from "./components/Tweet.vue";
import Filter from "./components/Filter.vue";

export default {
  name: "App",
  components: {
    Form,
    Tweet,
    Filter,
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
      // filteredTweet:{
      //   tweet_id:'',
      //   tweet_body:'',
      //   tweet_user:{
      //     user_id:'',
      //     user_name:'',
      //   }
      // }
    };
  },

  methods: {
    // receiveTweet（配列）…Formで入力された内容がはいってる
    appAction(receiveTweet) {
      // console.log(receiveTweet)
      // 配列AllTweetに対して、連想配列receiveTweetを追加する
      this.AllTweet.push(receiveTweet);
    },

    // ユーザー検索
    // ①ここで検索されたユーザー名をうけとる
    // ②ユーザー名と一致するツイートをまとめて配列にいれる
    // searchAction(searchUserName){
    //   const filteredTweet = this.AllTweet.filter(function (e) {
    //     return e.tweet_user.user_name === searchUserName;
    //   });
    //   console.log(filteredTweet);
    // },

    searchAction(n) {
      // 配列inputNameに、連想配列AllTweetからキーuser_nameに対する値だけを取得していれる
      // map()メソッド…連想配列から特定keyのvalueを取得
      let inputName = this.AllTweet.map((item) => item.tweet_user.user_name);
      console.log(inputName);


// 問題点：なんか値がはいらないとこがある
      // const filteredTweet = this.AllTweet.filter(function (e) {
      //   return e.tweet_user.user_name === n;
      // });
      // console.log(filteredTweet);

      const filteredTweet = this.AllTweet.filter(function () {
        return inputName === n;
      });
      console.log(filteredTweet);
    },
  },
};
</script>


