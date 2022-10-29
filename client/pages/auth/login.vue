<template>
  <v-container>
    <v-card class="mb-2 d-flex align-center justify-center mt-20">
      <v-row>
        <v-col cols="4">
          <p class="text-auth">FACEBOOK</p>
        </v-col>
        <v-col cols="8">
          <v-card rounded="xl" max-width="460" elevation="2" class="login-form">
            <v-card-text>
              <v-form class="form-login mt-5">
                <v-text-field
                  v-model="form.email"
                  type="email"
                  :rules="emailRules"
                  placeholder="e-mail"
                  required
                  filled
                  rounded
                ></v-text-field>

                <v-text-field
                  v-model="form.password"
                  :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                  :rules="[rules.required, rules.min]"
                  :type="show1 ? 'text' : 'password'"
                  placeholder="password"
                  hint="At least 3 characters"
                  counter
                  @click:append="show1 = !show1"
                  required
                  filled
                  rounded
                  @keyup.enter="login"
                ></v-text-field>
              </v-form>

              <v-btn
                :disabled="!valid"
                class="mr-2 btn-primary"
                rounded
                block
                large
                @click="login"
              >
                Login
              </v-btn>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-card>
  </v-container>
</template>

<script>
export default {
  layout: "auth",
  data: () => ({
    form: {
      email: "",
      password: "",
    },
    valid: true,
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    show1: false,
    rules: {
      required: (value) => !!value || "Required.",
      min: (v) => v.length >= 3 || "Min 3 characters",
      emailMatch: () => `The email and password you entered don't match`,
    },
  }),

  methods: {
    async login() {
      await this.$auth
        .loginWith("local", { data: this.form })
        .then(async (response) => {
          console.log("response :>> ", response);
        });
    },
  },
};
</script>

<style scoped>
.login-form {
  margin: auto;
  text-align: center;
  border-radius: 16px !important;
  box-shadow: none !important;
}

.mt-20 {
  margin-top: 60px !important;
}
.text-auth {
  text-align: center;
  font-size: 34px;
  color: blue;
  margin-top: 100px;
}
</style>
