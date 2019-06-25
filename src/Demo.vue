<template>
  <div class="wrapper">
    <h1>Vue Google Maps Zipcode Input</h1>
    <div>
      <Zipcode country="FR"></Zipcode>
    </div>
  </div>
</template>

<style lang="stylus" scoped>
.wrapper
  font-family sans-serif
</style>

<script>
import Zipcode from './Zipcode.vue';

export default {
  components: {
    Zipcode,
  }
}
</script>


