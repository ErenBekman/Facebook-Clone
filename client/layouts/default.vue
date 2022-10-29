<template>
  <v-app>
    <Navbar />
    <v-container>
      <Nuxt />
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  middleware: "auth",
  components: {
    Navbar: () => import("@/components/header/Navbar.vue"),
  },
  data() {
    return {};
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Questrial");
* {
  font-family: "Questrial";
}
</style>
