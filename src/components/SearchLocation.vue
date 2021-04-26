<template>
  <div>
    <div class="row justify-center q-px-md text-center">
      <div class="col-md-4 col-12">
        <GmapAutocomplete
          :options="{ fields: ['geometry'] }"
          @place_changed="setPlace"
          class="full-width"
        ></GmapAutocomplete>
      </div>
    </div>
    <div class="row q-py-md q-px-md justify-center">
      <div class="col-md-4 col-12">
        <q-btn
          color="positive"
          push
          label="Buscar"
          @click="addMarker"
          class="full-width"
        ></q-btn>
      </div>
    </div>
    <div class="row justify-center q-my-lg">
      <div class="col-md-8 col-12">
        <GmapMap
          :center="center"
          :zoom="12"
          style="width: 100%; height: 400px"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import * as VueGoogleMaps from "vue2-google-maps";
Vue.use(VueGoogleMaps, {
  load: {
    key: "AIzaSyCBqjJ6HUcv1-PphreVlNc0UW2Cl1mx8KU",
    libraries: "places",
  },
});

export default {
  name: "SearcLocation",
  data() {
    return {
      center: { lat: 0.487901, lng: -98.652978 },
      currentPlace: null,
      markers: [],
      places: [],
    };
  },
  mounted() {
    this.getGeoLocation();
  },
  methods: {
    getGeoLocation() {
      navigator.geolocation.getCurrentPosition((position) => {
        this.center = {
          lat: position.coords.latitude,
          lng: position.coords.longitude,
        };
      });
    },
    setPlace(place) {
      this.currentPlace = place;
      /* console.log(place); */
    },
    addMarker() {
      if (this.currentPlace) {
        const marker = {
          lat: this.currentPlace.geometry.location.lat(),
          lng: this.currentPlace.geometry.location.lng(),
        };
        this.markers.push({ position: marker });
        this.places.push(this.currentPlace);
        this.center = marker;
        this.currentPlace = null;
      }
    },
  },
};
</script>

<style>
</style>