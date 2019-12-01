<template lang="html">
  <div class="">
    <form class="fun-form" v-on:submit.prevent='handleForm'>
      <input class="text-input" type="number" name="" value="" v-model='text' required placeholder="insert your favourite number">
      <input class="search" type="submit" name="" value="search" >
    </form>

</div>
</template>

<script>
import {eventBus} from "../main.js"


export default {
  name: "fun-form",
  data(){
    return{
      text:''
    }
  },
  methods: {
    handleForm(){
      eventBus.$emit("to-translate", this.text)
    }
  }
}
</script>
@import url('https://fonts.googleapis.com/css?family=Permanent+Marker&display=swap')
<style lang="css" scoped>
.text-input{
  font-family: 'Permanent Marker', cursive;
  width: 200px;
  padding: 10px;
  font-size: 12px;
  border-radius: 5px;
  color: #00B282;
}

.search{
font-family: 'Permanent Marker', cursive;
background-color: #69D1C5;
padding: 12px;
border-radius: 4px;
color: #00B282;
}
form{
}
</style>
