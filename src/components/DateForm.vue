<template lang="html">
  <div class="">
    <form class="fun-form" v-on:submit.prevent = 'handleForm'>
      <input type="submit" name="" value="What hapened today">
    </form>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'date-form',
  data(){
    return{
      apiResponse:"",
    }
  },
  methods:{
    handleForm(){
      let today = new Date
      fetch(`https://numbersapi.p.rapidapi.com/${today.getMonth()}/${today.getDate()}/date?fragment=true&json=true`, {
	"method": "GET",
	"headers": {
		"x-rapidapi-host": "numbersapi.p.rapidapi.com",
		"x-rapidapi-key": "7c276f3231msha6b607e9767c23ep1c3116jsn3c40126e8814"
	}
}).then(response => response.json())
      .then(data => this.apiResponse = data)

      eventBus.$emit('date-form', this.apiResponse)


    }
  },

}
</script>

<style lang="css" scoped>
@import url('https://fonts.googleapis.com/css?family=Permanent+Marker&display=swap');

input{
  font-family: 'Permanent Marker', cursive;
  background-color: #69D1C5;
  padding: 12px;
  border-radius: 4px;
  color: #00B282;

}
</style>
