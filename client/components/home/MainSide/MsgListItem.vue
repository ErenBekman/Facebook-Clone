<template>
  <v-card width="800" outlined>
    <v-card-subtitle class="">
      <div>
        <p class="font-size-24">
          <v-avatar>
            <v-img
              class="elevation-6"
              src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460"
            ></v-img>
          </v-avatar>
          <span>
            {{ post.userId.username || this.$auth.user.username }}
          </span>
        </p>
      </div>
    </v-card-subtitle>
    <v-img
      v-if="post.img"
      class="white--text align-end p-5"
      height="400px"
      width="800px"
      :src="post.img"
    >
      <v-card-title class="text--white">{{ post.description }}</v-card-title>
    </v-img>
    <v-img
      v-else
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>{{ post.description }}</v-card-title>
    </v-img>

    <v-divider></v-divider>

    <v-card-subtitle>
      <div>
        <v-icon @click="likeButton(post._id)" size="x-large">mdi-heart</v-icon>

        {{ post.likes.length }} people like it
      </div>
    </v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  props: {
    post: {
      required: true,
      type: Object,
    },
  },

  data: () => ({
    show: false,
    userId: null,
  }),
  mounted() {
    this.userId = this.$auth.user._id;
  },

  methods: {
    async likeButton(id) {
      await this.$axios
        .$put(`/api/posts/${id}/like`, { userId: this.userId })
        .then((response) => {
          console.log("post like :>> ", response);
          window.location.reload(true);
        });
    },
  },
};
</script>

<style>
.text--black {
  color: black;
  margin-top: 20px;
}
.font-size-24 {
  font-size: 24px;
  color: black;
}
</style>
