<template>
   <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex xs12 sm8 md4>
            <v-card class="elevation-12">
              <v-toolbar dark color="primary">
                <v-toolbar-title>Sing Up form</v-toolbar-title>
                <v-spacer></v-spacer>
                <v-tooltip bottom>
                  <v-btn
                    slot="activator"
                    :href="source"
                    icon
                    large
                    target="_blank"
                  >
                    <v-icon large>code</v-icon>
                  </v-btn>
                  <span>Source</span>
                </v-tooltip>
                <v-tooltip right>
                  <v-btn slot="activator" icon large  target="_blank">
                    <v-icon large>mdi-codepen</v-icon>
                  </v-btn>
                  <span>Codepen</span>
                </v-tooltip>
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field prepend-icon="person" name="name" v-model="form.name" label="name" type="text"></v-text-field>
                  <v-text-field prepend-icon="email" name="email"   v-model="form.email" label="email" type="email"></v-text-field>
                  <v-text-field id="password" prepend-icon="lock" name="password"  v-model="form.password" label="Password" type="password"></v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="primary" type="submit" @click="registerUser">Signup</v-btn>
              </v-card-actions>
            </v-card>
          </v-flex>
        </v-layout>
      </v-container>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<script>
export default {
  name: "signup",
  data() {
    return {
      form: {
        name: "",
        email: "",
        password: ""
      }
    };
  },

  methods: {
    registerUser() {
      // alert("hello");
      axios.post("/register", this.$data.form).then(res => {
        console.log(res);
        let accessToken = res.data.auth.access_token;
        localStorage.setItem("token", accessToken);
        localStorage.setItem("user", res.data.user.name);
        window.singedIn = true;
      });
    }
  }
};
</script>

