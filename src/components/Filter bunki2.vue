<template>
  <div class="m-5">
    <!-- <button v-on:click="userFilter" class="btn btn-info">
      testさんのツイートを表示
    </button> -->

    <table class="table-primary">
      <tr>
        <th></th>
        <td>
          {{ TweetObj.tweet_user.user_name }} @
          {{ TweetObj.tweet_user.user_id }}
        </td>
      </tr>
      <tr>
        <th></th>
        <td>
          {{ TweetObj.tweet_body }}
        </td>
      </tr>
      <!-- ハートマーク -->
      <!-- ハートマークがクリックされたら、iineCountイベントが発生 -->
      <tr>
        <th></th>
        <td class="container">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-heart item"
            viewBox="0 0 16 16"
            v-on:click="iineCount"
          >
            <path
              d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"
            />
          </svg>
          <p class="item">{{ count }}</p>
          <!-- viewBox="x, y, width, height"
          x,yは左上からみたx座標とy座標の位置、そしてwidth,heightは描画エリアの幅(座標値)と高さ(座標値) -->
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-arrow-left-right item"
            viewBox="0 0 16 16"
          >
            <path
              fill-rule="evenodd"
              d="M1 11.5a.5.5 0 0 0 .5.5h11.793l-3.147 3.146a.5.5 0 0 0 .708.708l4-4a.5.5 0 0 0 0-.708l-4-4a.5.5 0 0 0-.708.708L13.293 11H1.5a.5.5 0 0 0-.5.5zm14-7a.5.5 0 0 1-.5.5H2.707l3.147 3.146a.5.5 0 1 1-.708.708l-4-4a.5.5 0 0 1 0-.708l4-4a.5.5 0 1 1 .708.708L2.707 4H14.5a.5.5 0 0 1 .5.5z"
            />
          </svg>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "Filter",
  props: {
    obj: Object,
  },
  data() {
    return {
      // Array.of()メソッド…配列を作成
      testTweet: {
        tweet_id: "",
        tweet_body: "",
        tweet_user: {
          user_id: "",
          user_name: "",
        },
      },
    };
  },
  // methods: {
  //   userFilter() {
  //     // 配列userNameに、連想配列obj（中身：連想配列AllTweet）からキーuser_nameに対する値だけを取得していれる
  //     // map()メソッド…配列を元に同じ要素数の配列を作成するメソッド。連想配列から特定keyのvalueを取得できる。
  //     // const userName = this.obj.map((item) => item.tweet_user.user_name);
  //     // console.log(userName);

  //     // こんなことがしたい
  //     // ①ユーザー名を入力する
  //     // ②変数を宣言←入力された値と一致するユーザー名をいれる
  //     // ③"test"の部分に変数をいれる    

  //     const testTweet = this.obj.filter(function (e) {
  //       return e.tweet_user.user_name === "test";
  //     });
  //     console.log(testTweet);

  //     // ここで分解するのではなく、ボタンをおしたらイベントが発火し、
  //     // App。VUEにてフィルターをかけ、そこでつくったTESTさんだけのツイートが
  //     // まとまった配列をFORMにかえしたらいいのでは

  //   },
  // },
};
</script>

