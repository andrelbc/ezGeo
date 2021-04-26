<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="shadow-up-5 bg-info">
      <q-toolbar class="container">
        <q-toolbar-title class="font"> ezGeo </q-toolbar-title>
        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: "MainLayout",
  data() {
    return {};
  },
};
</script>
