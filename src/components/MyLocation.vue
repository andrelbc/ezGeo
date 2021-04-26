<template>
  <div class="row justify-center">
    <div class="col-3">
      <q-btn
        flat
        label="Buscar endereço"
        class="bg-primary full-width"
        color="white"
        icon="search"
        size="lg"
        @click="getGeoLocation"
      ></q-btn>
      <div>latitude: {{ lat }}</div>
      <div>longitude: {{ lon }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyLocation",
  data() {
    return {
      lat: "",
      lon: "",
    };
  },
  methods: {
    getGeoLocation() {
      if (navigator.geolocation) {
          this.$q.loading.show()
        navigator.geolocation.getCurrentPosition(
          this.setPosition,
          this.errPosition
        );
      } else {
        alert("Geolocalização não disponivel :(");
      }
    },
    setPosition(position) {
      const coordenadas = position.coords;
      this.lat = coordenadas.latitude;
      this.lon = coordenadas.longitude;
      this.$q.loading.hide()
    },
    errPosition() {},
  },
};
</script>

<style>
</style>