<template>
  <v-container class="container">
    <v-row>
      <v-col cols="12">
        <UserInfo />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  components: {
    UserInfo: () => import("~/components/profile/UserInfo.vue"),
  },
  data: () => ({}),
};
</script>
