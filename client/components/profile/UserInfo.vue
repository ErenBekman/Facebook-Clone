<template>
  <v-row>
    <v-col cols="12">
      <UserProfile />
    </v-col>

    <v-col cols="3">
      <UserList />
    </v-col>
    <v-col cols="5">
      <MsgBox />
      <MsgList :postData="postData" />
    </v-col>
    <v-col cols="4">
      <FollowUser />
    </v-col>
  </v-row>
</template>

<script>
export default {
  components: {
    UserProfile: () => import("@/components/profile/UserProfile.vue"),
    UserList: () => import("@/components/profile/UserList.vue"),
    FollowUser: () => import("~/components/home/MainSide/FollowUser.vue"),
    MsgList: () => import("~/components/home/MainSide/MsgList.vue"),
    MsgBox: () => import("~/components/home/MainSide/MsgBox.vue"),
  },
  data: () => ({
    postData: {},
    userId: null,
  }),
  mounted() {
    this.getUserPost(this.$auth.user._id);
  },
  methods: {
    async getUserPost(userId) {
      console.log("this.userId 222 :>> ", userId);
      await this.$axios
        .$post("/api/posts/timeline/all", { userId: userId })
        .then((response) => {
          console.log("post user response :>> ", response);
          this.postData = response;
        });
    },
  },
};
</script>
