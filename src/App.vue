<template>

    <fun-form v-model="to_translate"></fun-form>

</template>

<script>
import {eventBus} from './main.js'
import FunForm from './components/FunForm.vue'

export default {
  name: 'app',
  data(){
    return{
      to_translate:"",
      translated:'',
      apiResponse:[]
    }
  },
  mounted(){
      eventBus.$on('to-translate', text => {
      this.to_translate = text
      this.transform(this.to_translate)
      // this.translate(this.to_translate)
    })

  },
  methods:{
    translate(){
      fetch(`https://api.funtranslations.com/translate/yoda.json?text=${this.to_translate}`)
        .then(result => result.json())
        .then(data => this.apiResponse = data )
    },
    transform(text){
      this.to_translate = text.replace(/ /g,"%20")
    }
  },
  components: {
    "fun-form": FunForm
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
