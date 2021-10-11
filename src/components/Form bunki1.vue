<template>
  <div class="m-5">
    <h2>{{ title }}</h2>
    <div>
      <input class="form-control m-5" type="text" v-model="input">
      <button class="btn btn-info m-5" v-on:click="doAction">ツイートする</button>
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
      input:'いまなにしてる？',
    }
  },
  methods:{
    // ツイートするボタンがおされたら、入力内容をApp.vueに送りresult-eventが発火する
    doAction(){
      this.$emit('result-event', this.input)
      // console.log(this.input)
    }
  }
}
</script>
