<template lang="html">
  <div class="">
    <form class="fun-form" v-on:submit.prevent='handleForm'>
      <input class="text-input" type="number" name="" value="" v-model='text' required placeholder="insert your favourite number">
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
.text-input{
  width: 200px
}
</style>
