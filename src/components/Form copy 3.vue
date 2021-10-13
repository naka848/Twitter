<template>
  <div class="m-5">
    <h2>{{ title }}</h2>



    <!-- ユーザー切り替えしたい！！！！！！！！！！！！！！ -->
    <button>click</button>
      <div v-if="a">aさんのとき</div>
      <div v-else>bさんのとき</div>
    



    <div>
      <!-- <input class="form-control m-5" type="text" v-model="input"> -->
      <textarea
        name="form"
        id=""
        class="formcontrol"
        cols="60"
        rows="5"
        placeholder="いまなにしとる？"
        v-model="TweetObj.tweet_body">
      </textarea>
      <br>
      <button class="btn btn-info" v-on:click="doAction">ツイートする</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  // プロパティを設定するもの
  props: {
    title: String,
  },
  data(){
    return{
      // input:'いまなにしてる？',
      TweetObj:{
        tweet_id:0,
        tweet_body:'',
        tweet_user:{
          user_id:'id',
          user_name:'ユーザー名'
        }
      }
    }
  },
  methods:{
    // ツイートするボタンがおされたら
    // ①tweet_idを１増やす
    // ②TweetObj（idと入力内容）をApp.vueに送り、result-eventが発火する
    doAction(){
      this.TweetObj.tweet_id += 1
      // （参照ではない）値をわたすために、新しいオブジェクトを定義する
      // Object.assign(target,sources)
      // target…コピー先オブジェクト。コピー元のプロパティを適用するもので、変更後に返されます。
      // sources…コピー元オブジェクト。適用したいプロパティを含むオブジェクトです。
      const sendTweet = Object.assign({},this.TweetObj)
      this.$emit('result-event', sendTweet)
      // console.log({})
      console.log(sendTweet)
    }
  }
}
</script>
