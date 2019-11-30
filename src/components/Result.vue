<template lang="html">
  <h1 v-if='result'>{{result.text}}</h1>
</template>

<script>


export default {
  name:'result',
  props:['result']
}
</script>

<style lang="css" scoped>
</style>
