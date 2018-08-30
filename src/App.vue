<template>
  <v-app>
    <v-toolbar>
    <v-toolbar-side-icon></v-toolbar-side-icon>
    <v-toolbar-title>
      <v-btn flat :to="{name:'home'}">
        {{title}}
      </v-btn>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">
      <v-btn flat v-for="(menu,index) in menus" :key="index" :to="{name:menu.route}">{{menu.name}}</v-btn>
    </v-toolbar-items>
  </v-toolbar>
  <router-view></router-view>

  </v-app>


</template>


<script>
export default {
  name: "App",
  data() {
    return {
      title: "Phonebook",
      menus: [
        { name: "Home", route: "home" },
        { name: "SignUp", route: "signup" },
        { name: "Login", route: "login" }
      ]
    };
  },

  methods: {
    getInfo() {
      axios.get("/user").then(res => {
        console.log(res.data);
      });
    }
  },
  mounted() {
    if (token) {
      let authMenu = [
        {
          name: "logout",
          route: "logout"
        }
      ];
      this.menus = authMenu;
    }
  }
};
</script>
