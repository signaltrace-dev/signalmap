<template>
  <div id="app">
      <mapwidget apikey="AIzaSyCnjHvBO9vjUQFI1s6P5dqcUnCozxB1HxQ" v-on:mapload="setMap" v-on:apiload="setApi"></mapwidget>
      <location v-for="loc in locations" v-bind:locationid="loc.id"></location>
  </div>
</template>

<script>
import MapWidget from './components/Map.vue'
import Location from './components/Location.vue'

export default {
  name: 'app',
  components: {
      'mapwidget': MapWidget,
      'location': Location
  },
  data: function(){
      return {
          locations: [],
          locationsVisible: [],
          gmap: {},
          gmapApi: {}
      };
  },
  computed: {
      markers: function(){
          let app = this;
          let markers = [];

          app.locationsVisible.forEach(function(loc){
              var myLatlng = new app.gmapApi.maps.LatLng(loc.lat, loc.lng);

              var marker = new app.gmapApi.maps.Marker({
               position: myLatLng,
               //map: app.gmap,
               title: 'Hello World!'
           });
          });

          return markers;
      }
  },
  methods: {
      loadLocations: function(){
          this.locations = [{
              lat: '44.33328',
              lng: '-89.132008',
              addressLine1: 'fdsafds',
              addressLine2: '',
              city: '',
              state: '',
              zip: '',
              url: '',
              phone: '',
              name: 'A Place',
              description: '',
              id: 1
          },
          {
              lat: '44.968046',
              lng: '-94.420307',
              addressLine1: '123 Fake St',
              addressLine2: 'Apt 1',
              city: 'Somewhere',
              state: 'AL',
              zip: '90210',
              url: '',
              phone: '',
              name: 'Somewhere Something',
              description: '',
              id: 2
          }];
          this.locationsVisible = this.locations;
          // Grab a list of locations from a provided data source
      },
      getLocation: function(locationId){
          var app = this;

          let location = {};
          location = app.locations.find(function(l){
              return l.id === locationId;
          });

          return location;
      },
      setMap: function(mapInstance){
          this.gmap = mapInstance;
      },
      setApi: function(apiInstance){
          this.gmapApi = apiInstance;
      }
  },
  mounted: function(){
      this.loadLocations();
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
