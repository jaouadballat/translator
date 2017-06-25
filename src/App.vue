<template>
  <div class="text-center" id="wordtranslator">
    <h1>Word Translator</h1>
    <h5 class="text-muted">Coded By Jaouad Ballat</h5>
    <div class="col-md-6 col-md-offset-3">
      <TranslateForm v-on:formSubmit="translate" ></TranslateForm>
      <TranslateOutput :translated="translatedText"></TranslateOutput>
    </div>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm.vue'
import TranslateOutput from './components/TranslateOutput.vue'


export default {

  components:{
    TranslateForm,
    TranslateOutput
  },
  name: 'wordtranslator',
  data () {
    return {
    translatedText:'',
    }
  },
  methods:{
    translate(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170625T172659Z.0cea1c0c7fff33f6.ad9dec2f35167aec0e91c0a859f8753401df255f&lang='+language+'&text='+text).then(data => {
         this.translatedText = data.body.text[0]
        })
    }
  }
}
</script>

<style>

h5{
  margin-bottom: 100px;
}

</style>
