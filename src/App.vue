<template>
  <div id="app">
    <h1 class="text-muted">在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <TranslatorForm v-on:fromsubmit='translatorText'></TranslatorForm>
    <TranslatorOutPut v-text="Texttranslator"></TranslatorOutPut>
  </div>
</template>

<script>

import TranslatorForm from './components/TranslatorForm'
import TranslatorOutPut from './components/translatorOutPut'

export default {
  name: 'App',
  data:function(){
    return{
      Texttranslator:""
    }
  },
  components: {
    TranslatorForm,
    TranslatorOutPut
  },
  methods: {
    // 接收传参
    translatorText:function(text,language){
      // alert(language);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180417T071213Z.80eed91efbe82543.89587e0b6571b7b6826a72123c7c83979940e682&lang=' + language + '&text=' + text).then((response)=>{
        // console.log(response.body.text[0]);
        this.Texttranslator = response.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
