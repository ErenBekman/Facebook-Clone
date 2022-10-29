<template>
  <v-app-bar app color="accent" height="110" flat>
    <v-container class="py-3 fill-height">
      <v-responsive max-width="260">
        <p class="text">Facebook</p>
        <!-- <v-text-field
          dense
          flat
          hide-details
          rounded
          solo-inverted
          background-color="primary"
          placeholder="search.."
          class="mb-10"
        ></v-text-field> -->
      </v-responsive>

      <v-spacer></v-spacer>

      <v-card class="mb-10">
        <v-bottom-navigation>
          <v-btn to="/home">
            <span>Home</span>

            <v-icon>mdi-home</v-icon>
          </v-btn>

          <v-btn to="/profile">
            <span>Profile</span>

            <v-icon>mdi-account</v-icon>
          </v-btn>
        </v-bottom-navigation>
      </v-card>

      <v-spacer></v-spacer>

      <v-menu offset-y open-on-hover :nudge-width="150">
        <template v-slot:activator="{ attrs, on }">
          <v-btn icon v-bind="attrs" v-on="on" class="mb-10">
            <v-avatar color="primary" size="55">
              <span class="white--text text-h5"> {{ short_name }} </span>
            </v-avatar>
          </v-btn>
        </template>

        <v-list dense class="text-left">
          <v-list-item>
            Hi! <span class="font-weight-bold ml-2"> {{ username }} </span>
          </v-list-item>
          <v-divider class="my-1"></v-divider>
          <v-list-item link @click.prevent="logout()" to="/auth/login">
            <v-list-item-icon class="mr-2"
              ><v-icon small>mdi-logout-variant</v-icon></v-list-item-icon
            >
            <v-list-item-title>Cikis yap</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-container>
  </v-app-bar>
</template>

<script>
export default {
  data: () => ({
    username: null,
    short_name: null,
  }),

  mounted() {
    this.username = this.$auth ? this.$auth.user.username : "X";
    this.short_name = this.username[0];
  },
  methods: {
    async logout() {
      await this.$auth.logout();
    },
  },
};
</script>

<style>
.text {
  font-size: 26px;
  color: white;
  font-weight: 800;
}
</style>
