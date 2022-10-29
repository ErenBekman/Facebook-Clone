<template>
  <v-card class="mx-auto">
    <v-card-text class="d-flex">
      <v-avatar class="mt-3">
        <v-img
          class="elevation-6"
          src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
        ></v-img>
      </v-avatar>
      <v-textarea
        class="mx-2"
        :label="`What's your mind, ${username}?`"
        rows="1"
        prepend-icon="mdi-comment"
        v-model="PostData.description"
      ></v-textarea>
    </v-card-text>

    <v-card-actions>
      <v-row>
        <v-col cols="3">
          <v-btn text dark color="indigo">
            <v-icon dark> mdi-camera </v-icon>
            <span>Photo</span>
            <v-file-input
              v-model="PostData.img"
              label="File input"
            ></v-file-input>
          </v-btn>
        </v-col>
        <v-col cols="3">
          <v-btn text dark color="indigo">
            <v-icon dark> mdi-tag </v-icon>
            <span>Tag</span>
          </v-btn>
        </v-col>
        <v-col cols="3">
          <v-btn text dark color="indigo">
            <v-icon dark> mdi-map </v-icon>
            <span>Location</span>
          </v-btn>
        </v-col>
        <v-col cols="3">
          <v-btn text color="primary" outlined rounded @click="addPost">
            <v-icon dark> mdi-plus </v-icon>
            <span>Share</span>
          </v-btn>
        </v-col>
      </v-row>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  components: {
    MsgBox: () => import("~/components/home/MainSide/MsgBox.vue"),
  },

  data: () => ({
    PostData: {
      userId: null,
      description: "",
      img: {},
    },
    username: "",
  }),
  mounted() {
    this.PostData.userId = this.$auth.user._id;
    this.username = this.$auth.user.username;
  },
  methods: {
    async addPost() {
      let formData = new FormData();
      Object.keys(this.PostData).forEach((element) => {
        formData.append(element, this.PostData[element]);
      });

      await this.$axios
        .$post("/api/posts", formData, {
          headers: { "Content-Type": "multipart/form-data" },
        })
        .then((response) => {
          console.log("post response :>> ", response);
        });
    },
  },
};
</script>
