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
      this.translate()
    })

  },
  methods:{
    translate(){
      fetch("https://numbersapi.p.rapidapi.com/1730/math?fragment=true&json=true", {
	"method": "GET",
	"headers": {
		"x-rapidapi-host": "numbersapi.p.rapidapi.com",
		"x-rapidapi-key": "7c276f3231msha6b607e9767c23ep1c3116jsn3c40126e8814"
	}
})
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
