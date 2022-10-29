<template>
  <v-container class="container">
    <v-row>
      <v-col cols="4">
        <LeftSide />
      </v-col>
      <v-col cols="8">
        <MainSide />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {
    LeftSide: () => import("~/components/home/LeftSide/ListItem.vue"),
    MainSide: () => import("~/components/home/MainSide/Main.vue"),
  },
  data: () => ({}),
};
</script>
