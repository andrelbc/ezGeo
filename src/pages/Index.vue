<template>
  <q-page class="container">
    <div class="row justify-center">
      <div class="col-md-2 q-ma-xl">
        <img alt="Quasar logo" src="~assets/navegacao.svg" />
      </div>
    </div>

    <div>
      <Searchlocation />
    </div>
  </q-page>
</template>

<script>
/* import MyLocation from "components/MyLocation.vue"; */
import Searchlocation from "components/SearchLocation.vue";
export default {
  name: "PageIndex",
  components: {
/*     MyLocation, */
    Searchlocation,
  },
};
</script>
<style scoped>
img:not(.png) {
  width: 100%;
}
</style>
