<template>
  <div id="translatorForm" class="row">
      <div class="col-md-6 col-md-offset-3">
          <form @submit="fromSubmit" class="well form-inline" id="transForm">
            <input class="form-control" type="text" placeholder="输入需要翻译的内容" v-model="TextTotranslator">
                <select v-model="language" class="form-control">
                    <option value="en">English</option>
                    <option value="zh">Chinese</option>
                    <option value="ru">Russian</option>
                    <option value="ko">Korea</option>
                    <option value="ja">Japanese</option>
                </select>
            <input type="submit" value="翻译" class="btn btn-primary">
        </form>
      </div>
  </div>
</template>

<script>

export default {
  name: 'translatorForm',
  data:function(){
      return {
          TextTotranslator:"",
          language:""
      }
  },
  methods:{
    fromSubmit:function(e){
        // 传参app.vue
        this.$emit("fromsubmit", this.TextTotranslator, this.language)
        // 传入e，取消刷新事件
        e.preventDefault();
    }
  },
  created:function() {
      this.language = "en"
  }
}
</script>

<style>
    #transForm{
        border: 1px solid #ccc;
        border-radius: 10px;
    }
</style>
