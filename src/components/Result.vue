<template lang="html">
  <div class="">
  <h1 v-if='result'>{{result.text}}</h1>
  <h2 v-if='result.year'>same day at year:{{result.year}}</h2>
</div>
</template>

<script>


export default {
  name:'result',
  props:['result']
}
</script>

<style lang="css" scoped>
</style>
