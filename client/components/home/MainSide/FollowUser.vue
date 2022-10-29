<template>
  <v-card class="mx-auto" max-width="400" tile>
    <v-list dense>
      <v-subheader>FOLLOW RECOMMENDED</v-subheader>
      <v-list-item-group
        color="primary"
        v-for="(item, index) in userData"
        :key="index"
      >
        <v-list-item class="mt-3">
          <v-avatar>
            <v-img
              class="elevation-6"
              src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
            ></v-img>
          </v-avatar>

          <v-list-item-content class="ml-1">
            <v-list-item-title> {{ item.username }}</v-list-item-title>
            {{ item.email }}
          </v-list-item-content>

          <v-btn
            text
            color="primary"
            outlined
            rounded
            @click="follow(item._id)"
          >
            <v-icon dark> mdi-plus </v-icon>
            <span>Follow</span>
          </v-btn>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    userData: {},
    userId: null,
  }),
  mounted() {
    this.getUserList();
    this.userId = this.$auth.user._id;
  },
  methods: {
    async getUserList() {
      await this.$axios.$get("/api/users").then((response) => {
        let filterData = response.filter(
          (eleman) =>
            eleman.followings.length == 0 && eleman._id != this.$auth.user._id
        );
        this.userData = filterData;
      });
    },
    async follow(userId) {
      console.log("userId :>> ", userId);
      await this.$axios
        .$put(`/api/users/${this.userId}/follow`, { userId: userId })
        .then((response) => {
          console.log("follow response :>> ", response);
          window.location.reload(true);
        });
    },
  },
};
</script>

<style>
.red {
  color: #000;
  background-color: aquamarine;
}
</style>
