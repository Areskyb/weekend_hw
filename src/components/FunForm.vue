<template lang="html">
  <form class="fun-form" v-on:submit.prevent='handleForm'>
    <input type="number" name="" value="" v-model='text'>
    <input type="submit" name="" value="search">
  </form>

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
