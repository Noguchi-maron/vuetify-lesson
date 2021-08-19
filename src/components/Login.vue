<template>
<v-app>
  <v-row justify="center" align="center">
    <v-col cols="6" md="4">
      <v-card class="px-10 py-15">
        <p>ログイン</p>
        <v-text-field v-model="userId" label="ユーザー名" clearable>
        </v-text-field>
        <v-text-field v-model="password" label="パスワード" clearable :type=toggle.type :append-icon=toggle.icon @click:append="passwordShow=!passwordShow">
        </v-text-field>
        <v-row class="mt-5">
        <v-btn elevation="0" color="primary" @click="login">ログイン</v-btn>
        <v-spacer></v-spacer>
        <v-btn outlined @click="signUp">新規登録</v-btn>
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</v-app>
</template>
<script>

export default({
  props: {
    usersData: Array
  },
  data () {
    return {
      userId: '',
      password: '',
      passwordShow: false
    }
  },
  computed: {
    toggle () {
      const icon = this.passwordShow ? 'mdi-eye' : 'mdi-eye-off'
      const type = this.passwordShow ? 'text' : 'password'
      return {icon, type}
    }
  },
  methods: {
    signUp () {
      this.$emit("sign-up")
    },
    login () {
      if(
        this.userId === this.usersData[0].userId && 
        this.password === this.usersData[0].password
        ) {
          alert('ログインしました')
          this.userId = ''
          this.password = ''
        } else {
          alert('ログインできません')
        }
    }
  }
})
</script>
