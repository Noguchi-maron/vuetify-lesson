<template>
  <v-app>
  <v-row justify="center" align="center">
    <v-col cols="6">
      <v-card class="px-10 py-15">
        <p>新規登録</p>
        <v-text-field v-model="lastName" label="氏" clearable></v-text-field>
        <v-text-field v-model="firstName" label="名" clearable></v-text-field>
        <v-text-field v-model="userId" label="ユーザー名" clearable>
        </v-text-field>
        <v-text-field v-model="password" label="パスワード" clearable>
        </v-text-field>
        <v-btn color="primary" class="mt-5" @click="signUp">新規登録</v-btn>
      </v-card>
    </v-col>
  </v-row>
</v-app>
</template>

<script>

export default ({
  data () {
    return {
      users: [],
      lastName: '',
      firstName: '',
      userId: '',
      password: ''
    }
  },
  methods: {
    signUp () {
      this.users.push({
        lastName : this.lastName,
        firstName: this.firstName,
        userId: this.userId,
        password: this.password
      })
      this.$emit('users', this.users)
    }
  }
})
</script>

