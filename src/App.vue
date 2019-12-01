<template>
  <div class="app">
    <h1>Ask for info</h1>
    <div class="forms">
    <fun-form v-model="to_translate"></fun-form>
    <date-form></date-form>
  </div>
    <result class="result" :result="this.apiResponse"></result>
  </div>

</template>

<script>
import {eventBus} from './main.js'
import DateForm from './components/DateForm.vue'
import FunForm from './components/FunForm.vue'
import Result from './components/Result.vue'

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

    eventBus.$on('date-form', data => {
        this.apiResponse = data
    })

  },
  methods:{
    translate(){
      fetch(`https://numbersapi.p.rapidapi.com/${this.to_translate}/math?fragment=true&json=true`, {
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
    "fun-form": FunForm,
    "result": Result,
    "date-form": DateForm
  }
}
</script>

<style>
h1{
  text-align: center;
  color: #00B282
}
.app{
  margin-top: 10%;
  }

.forms{
  display: flex;
  justify-content: space-around;
}
.result{
  text-align: center
}
</style>
