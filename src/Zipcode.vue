<template>
  <div>
    <input v-model="zipcode" ref="autocomplete" type="text" placeholder="zipcode">
  </div>
</template>

<script>
import { geocode, filterComponents } from './geocode.js';

export default {
  props: {
    country: {type: String}
  },
  data: function() {
    return {
      zipcode: '',
    };
  },
  methods: {

  },
  mounted() {
    var options = {
      types: ['(regions)'],
    };

    if (this.country) {
      options.componentRestrictions = {
        country: this.country,
      };
    }

    this.autocomplete = new google
      .maps.places.Autocomplete(this.$refs.autocomplete, options);

    this.autocomplete.addListener('place_changed', () => {
      let place = this.autocomplete.getPlace();

      var latlng = {
        lat: place.geometry.location.lat(),
        lng: place.geometry.location.lng(),
      };

      geocode(latlng).then(results => {
        var zipcode = filterComponents(results, 'postal_code');
        var country = filterComponents(results, 'country');

        this.$emit('selected', {
          place,
          latlng,
          zipcode,
          country,
        });
      });

      this.$set(this.$data, 'zipcode', '');
    });
  },
}
</script>

