<template>
  <div id="app" class="container">
    <center>
      <h1>Word Traslator</h1>
      <small>Powered by Kimoo with VueJS</small>
    </center>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <translate-output v-text="translatedText"></translate-output>
  </div>
</template>

<script>
  import TranslateForm from './components/TranslateForm';
  import TranslateOutput from './components/TranslateOutput.vue'
  export default {
    name: 'app',
    components: {
      TranslateForm,
      TranslateOutput
    },
    data(){
      return{
        translatedText:''
      }
    },
    methods:{
      translateText:function(text,language){
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171011T200550Z.03639e722d22a7d8.f2b3be5b6a74331432579ad39e2e73605140fb8f&lang='+language+'&text='+text)
        .then((response) => {
          this.translatedText= response.body.text[0];
        }
        );
      }
    }
  }
</script>

<style>
  #app {}
</style>
