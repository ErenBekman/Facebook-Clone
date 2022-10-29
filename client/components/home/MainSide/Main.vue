<template>
  <div>
    <div>
      <MsgBox />
    </div>
    <div class="mt-5">
      <MsgList :postData="postData" />
    </div>
  </div>
</template>

<script>
export default {
  components: {
    MsgBox: () => import("~/components/home/MainSide/MsgBox.vue"),
    MsgList: () => import("~/components/home/MainSide/MsgList.vue"),
  },
  data: () => ({
    postData: {},
  }),
  mounted() {
    this.getPost();
  },
  methods: {
    async getPost() {
      await this.$axios.$get("/api/posts").then((response) => {
        console.log("post response :>> ", response);
        this.postData = response;
      });
    },
  },
};
</script>
