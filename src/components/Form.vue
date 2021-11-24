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
        v-model="data.TweetObj.tweet_body"
      >
      </textarea>
      <br />
      <button class="btn btn-info" v-on:click="doAction">ツイートする</button>
    </div>
  </div>
</template>

<script>
import { onUpdated, reactive } from "vue";

export default {
  name: "Form",
  props: {
    title: String,
    user: Object,
  },

  setup(props,context) {
    const data = reactive({
      TweetObj: {
        tweet_id: 0,
        tweet_body: "",
        tweet_user: {
          user_id: "id",
          user_name: "test",
        },
      },
    });
    console.log(props.user);

    onUpdated(()=>{
      // console.log(data.TweetObj.tweet_user);
    })

    const doAction = () => {
      data.TweetObj.tweet_id += 1;

      data.TweetObj.tweet_user = props.user;

      const sendTweet = Object.assign({}, data.TweetObj);
      context.emit("result-event", sendTweet);
      console.log(sendTweet);
    };

    return {
      data,
      doAction,
    };
  },

  // data(){
  //   return{
  //     TweetObj:{
  //       tweet_id:0,
  //       tweet_body:'',
  //       tweet_user:{
  //         user_id:'id',
  //         user_name:'test'
  //       }
  //     },
  //   }
  // },

  // methods: {
  //   doAction() {
  //     this.data.TweetObj.tweet_id += 1;
  //     this.data.TweetObj.tweet_user = this.data.user;
  //     const sendTweet = Object.assign({}, this.data.TweetObj);
  //     this.$emit("result-event", sendTweet);
  //   },
  // },

  // methods:{
  //   // ツイートするボタンがおされたら
  //   // ①tweet_idを１増やす
  //   // ②TweetObj（idと入力内容）をApp.vueに送り、result-eventが発火する
  //   doAction(){
  //     this.TweetObj.tweet_id += 1
  //     this.TweetObj.tweet_user = this.user;
  //     // （参照ではない）値をわたすために、新しいオブジェクトを定義する
  //     // Object.assign(コピー先オブジェクト,コピー元オブジェクト)
  //     const sendTweet = Object.assign({},this.TweetObj)
  //     this.$emit('result-event', sendTweet)
  //   },
  // }
};
</script>
