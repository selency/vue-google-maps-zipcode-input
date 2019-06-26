# vue-google-maps-zipcode-input

This component provides an easy way to handle google maps zipcode autocompletion wih Vue. Due to various restrictions on the Google Maps Platform, reverse geocoding may be required to end up with an actual zipcode, which this component handles.

![demo](https://user-images.githubusercontent.com/1770991/60190764-7d08e600-9833-11e9-94cd-67dc13a95c19.gif)

## Usage

The [Demo.vue](src/Demo.vue) provides an example integration of this component.

This component uses slots so you can provide your own `input`. The only requirement is to add `ref="autocomplete"` on the input element.

```html
<!-- Google Maps need to be loaded on your page with the places library enabled -->
<script type="text/javascript" src="https://maps.googleapis.com/maps/api/js?key=1234&libraries=places"></script>

<!-- ... -->

<Zipcode @selected="zipcodeSelected" country="FR">
  <input type="text" ref="autocomplete">
</Zipcode>
```

```javascript
import Zipcode from './Zipcode.vue';

export default {
  methods: {
    zipcodeSelected(location) {
      console.log(location);
    },
  },
  components: {
    Zipcode,
  }
}
```

## Props

* `country` can be used to restrict the suggestions scope

## Events

* `selected`
