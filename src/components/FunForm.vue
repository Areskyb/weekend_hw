<template lang="html">
  <form class="fun-form" v-on:submit.prevent='handleForm'>
    <textarea name="name" rows="8" cols="80" v-model="text"></textarea>
    <input type="submit" name="" value="translate">
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
