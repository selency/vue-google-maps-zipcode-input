<template>
  <div class="wrapper">
    <h1>Vue Google Maps Zipcode Input</h1>
    <div>
      <p>Locations are logged to console once selected</p>
      <Zipcode @selected="zipcodeSelected" country="FR">
        <input v-model="zipcode" type="text" ref="autocomplete">
      </Zipcode>
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
  data() {
    return {
      zipcode: '',
    }
  },
  methods: {
    zipcodeSelected(location) {
      this.$set(this.$data, 'zipcode', '');
      console.log(location);
    },
  },
  components: {
    Zipcode,
  }
}
</script>


