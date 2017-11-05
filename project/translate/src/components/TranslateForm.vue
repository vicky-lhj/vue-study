<template>
  <div class="row" id="translate-form">
  <div class="col-md-12" id="bgForm">
   <form @submit="formSubmit">
   <input class="form-control mr-sm-2" type="text" v-model="textToTranlate" placeholder="输入需要翻译的内容">
   <br/>
  <select v-model="language" class="form-control">
    <option value="en">English</option>
    <option value="ru">Russian</option>
    <option value="ko">Korean</option>
    <option value="ja">Janpenese</option>
  </select>
  <br/>
  <input class="btn btn-primary btn-lg btn-block" type="submit" value="翻译">   
  </form>   
  </div>
  </div>
</template>

<script>
export default {
  name: 'translate-form',
  data:function(){
    return {
      textToTranlate:"",
      language:""
    }
  },
  methods:{
     formSubmit:function(e){
      if (!this.textToTranlate=="") {
      this.$emit("formSubmit",this.textToTranlate,this.language);        
    }else{
      alert("请输入要翻译的内容");
    }

      e.preventDefault();
     }
  },
  created:function(){
    this.language="en";
  }
}
</script>

<style>
</style>
