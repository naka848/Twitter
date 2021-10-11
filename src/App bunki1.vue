// コンポーネントで出力される内容を扱う
<template>
  <div id="app">
    <Form title="ひとりごと"
      v-on:result-event="appAction" />
    <!-- <Tweet v-bind:tweet="t" /> -->
    <!-- <Tweet v-bind:hairetu="[123,456,789]" /> -->
    <Tweet>
      <p>kk</p>
    </Tweet>
  </div>
</template>

<script>
import Form from './components/Form.vue'
import Tweet from './components/Tweet.vue'

export default {
  name: 'App',
  components: {
    Form,
    Tweet,
  },
  // コンポーネントが読み込まれたときに動く部分
  // tの定義、宣言をする
  data(){
    return{
      // t:'',
      // items:[{tweet:'t'}]
    }
  },
  methods: {
    // message＝Formで入力された内容
    // Formで入力された内容をdata()のtweetにわたす
    appAction(message){
      // console.log(message)
      this.t = message
      console.log(this.t)
    }
  }
}
</script>

<style>

</style>


