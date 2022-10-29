<template>
  <v-card class="mx-auto">
    <v-img
      src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
      class="profile-img"
    ></v-img>

    <v-card-actions>
      <v-list-item class="grow">
        <v-chip class="ma-2" color="primary">
          <v-icon class="mr-2">mdi-account-arrow-up</v-icon>
          <span class="font-weight-bold mr-2">
            {{ this.$auth.user.followers.length }}
          </span>
          follower
        </v-chip>
        <v-chip class="ma-2" color="primary">
          <v-icon class="mr-2">mdi-account-arrow-up</v-icon>
          <span class="font-weight-bold mr-2"
            >{{ this.$auth.user.followings.length }}
          </span>
          following
        </v-chip>
        <v-list-item-content>
          <v-list-item-title></v-list-item-title>
        </v-list-item-content>

        <div class="d-flex flex-column">
          <v-img
            class="elevation-6 grey lighten-2 avatar-profile"
            src="https://avataaars.io/?avatarStyle=Transparent&topType=ShortHairShortCurly&accessoriesType=Prescription02&hairColor=Black&facialHairType=Blank&clotheType=Hoodie&clotheColor=White&eyeType=Default&eyebrowType=DefaultNatural&mouthType=Default&skinColor=Light"
            width="100"
            height="100"
            aspect-ratio="1"
          ></v-img>

          <p class="text-center mt-2">{{ this.$auth.user.username }}</p>
        </div>

        <v-row align="center" justify="end">
          <v-icon class="mr-1"> mdi-heart </v-icon>
          <span class="subheading mr-2">256</span>
          <v-icon class="mr-1"> mdi-share-variant </v-icon>
          <span class="subheading">45</span>
        </v-row>
      </v-list-item>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data: () => ({}),
  mounted() {},
};
</script>

<style>
.profile-img {
  padding-top: 15px !important;
  height: 300px;
}

.avatar-profile {
  border-radius: 50%;
}
</style>
