<template>
  <v-container fluid class="container">
    <v-row>
      <v-col cols="2">
        <LeftSide />
      </v-col>
      <v-col cols="6">
        <MainSide />
      </v-col>
      <v-col cols="4">
        <FollowUser />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {
    LeftSide: () => import("~/components/home/LeftSide/ListItem.vue"),
    MainSide: () => import("~/components/home/MainSide/Main.vue"),
    FollowUser: () => import("~/components/home/MainSide/FollowUser.vue"),
  },
  data: () => ({}),
};
</script>
