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
      <v-container pa-0>
      <v-btn block text x-large v-for="btn in menuBtns" :key="btn" @click="currentView=btn">{{ btn }}</v-btn>
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

export default {
  name: 'App',
  components: {
    Login,
    SignUpPage,
    Home
  },
  data: () => ({
    drawer: null,
    toolBtns: ['Login', 'MyPage'],
    menuBtns: ['Home', 'New Trip', 'Schedule', 'Photo', 'Login'],
    currentView: 'Login',
    users: [],
    photoUrl: [
      //新幹線
      'https://1.bp.blogspot.com/-CZhDpH9AENw/WTd5T6ADZtI/AAAAAAABEuw/epxCOLW9e0QvxnGxHjquTneZkhotr294gCLcB/s400/travel_bus_train_student.png',
      //富士山
      'https://3.bp.blogspot.com/-WiNPt0_l3lc/U0pTNIhcmUI/AAAAAAAAfF4/BW1m-kFqMzI/s400/fujisan_shikaku.png',
      //夕日
      'https://3.bp.blogspot.com/-WiNPt0_l3lc/U0pTNIhcmUI/AAAAAAAAfF4/BW1m-kFqMzI/s400/fujisan_shikaku.png'
    ]
  }),
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
