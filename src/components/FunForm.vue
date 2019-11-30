<template lang="html">
  <div class="">
    <h3>Get info from you favourite number</h3>  
    <form class="fun-form" v-on:submit.prevent='handleForm'>
      <input type="number" name="" value="" v-model='text'>
      <input type="submit" name="" value="search">
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

<style lang="css" scoped>
</style>
