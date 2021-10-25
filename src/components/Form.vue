<template>
  <div class="m-5">
    <h2>{{ title }}</h2>
    <div>
      <textarea
        name="form"
        id=""
        class="form-control"
        cols="60"
        rows="5"
        placeholder="いまなにしとる？"
        v-model="TweetObj.tweet_body"
      >
      </textarea>
      <br>
      <button class="btn btn-info" 
        v-on:click="doAction">ツイートする</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  props: {
    title: String,
  },
  data(){
    return{
      TweetObj:{
        tweet_id:0,
        tweet_body:'',
        tweet_user:{
          user_id:'id',
          user_name:'test'
        }
      },
      
      searchName:"",
    }
  },
  methods:{
    // ツイートするボタンがおされたら
    // ①tweet_idを１増やす
    // ②TweetObj（idと入力内容）をApp.vueに送り、result-eventが発火する
    doAction(){ 
      this.TweetObj.tweet_id += 1
      // （参照ではない）値をわたすために、新しいオブジェクトを定義する
      // Object.assign(コピー先オブジェクト,コピー元オブジェクト)
      const sendTweet = Object.assign({},this.TweetObj)
      this.$emit('result-event', sendTweet)
    },

  }
}
</script>
