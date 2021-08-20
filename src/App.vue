<template>
  <v-app>
    <header>
      <v-toolbar absolute flat>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>Vuetify</v-toolbar-title>
        <v-spacer></v-spacer>
        
      </v-toolbar>
    </header>
      
    <v-navigation-drawer absolute v-model="drawer" temporary>
      <v-container :class="{ 'xs-style': xsStyle }" class="pa-0">
        <v-list-item-group>
          <v-list-item block text x-large v-for="list in menuLists" :key="list" @click="currentView=list" class="pl-10">{{ list }}</v-list-item>

        </v-list-item-group>
      </v-container>
    </v-navigation-drawer>
    <v-main>
      <component :is="currentView" @sign-up=signUp @users=usersData :usersData="users"></component>
    </v-main>
  </v-app>
</template>

<script>
import Login from './components/Login.vue'
import SignUpPage from './components/SignUpPage.vue'
import Home from './components/Home.vue'
import Photo from './components/Photo.vue'

export default {
  name: 'App',
  components: {
    Login,
    SignUpPage,
    Home,
    Photo
  },
  data: () => ({
    drawer: null,
    menuLists: ['Home', 'Photo', 'Login'],
    currentView: 'Home',
    users: [],
    
  }),
  computed: {
    xsStyle () {
        if (this.$vuetify.breakpoint.xs) {
        return true;
      } else {
        return false;
      }
    }
  },
  methods: {
    signUp () {
      this.currentView='SignUpPage'
    },
    usersData (data) {
      this.users = data 
      this.currentView='Login'
    }
  }
};
</script>

<style>
  .xs-style {
    margin-top: 60px;
  }
</style>