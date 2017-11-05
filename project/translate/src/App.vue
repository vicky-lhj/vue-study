<template>
  <div id="app">
 <div class="card">
  <h3 class="card-header">在线翻译</h3>
  <div class="card-body">
     <translate-form @formSubmit="translateText"></translate-form>
  </div>
  <div class="card-body">
   <translate-output v-text="translatedText"></translate-output>
  </div>
  <div class="card-footer text-muted">
    © 2014–2017
  </div>
</div>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data:function(){
   return{
    translatedText:"welcome!"
   }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods:{
    translateText:function(text,language){
      this.translatedText="翻译中..."
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171105T115332Z.01ebd61507db22d0.d5728f1614a55cfda5a7391720d1cdc3a41f151a&lang='+language+'&text='+text)
      .then((response)=>{
        // console.log(response.body.text[0]);
        this.translatedText=response.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  width: 460px;
  margin: auto;
  padding: 20px;
}
</style>
