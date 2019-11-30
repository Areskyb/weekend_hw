<template lang="html">
  <div class="">
    <form class="fun-form" v-on:submit.prevent = 'handleForm'>
      <input type="submit" name="" value="What hapened today">
    </form>
  </div>
</template>

<script>
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

    }
  },

}
</script>

<style lang="css" scoped>
</style>
