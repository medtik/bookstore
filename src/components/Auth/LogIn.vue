<template>
  <v-card-text @keyup.enter='logIn'>
    <p class="text-xs-center">
      Login: test
      <br>
      Password: test
    </p>
    <v-form v-model="valid" ref="form" lazy-validation>
      <v-text-field
        label="Username"
        v-model="name"
        :rules="nameRules"
        required
      ></v-text-field>
      <v-text-field
        label="Password"
        v-model="pass"
        :rules="passRules"
        required
      ></v-text-field>
    </v-form>
    <v-layout>
      <v-btn small @click='reg'>Регистрация</v-btn>
      <v-spacer></v-spacer>
      <v-btn small @click='logIn'>Войти</v-btn>
    </v-layout>
  </v-card-text>
</template>

<script>
export default {
  name: 'LogIn',
  data: () => ({
    valid: true,
    name: '',
    pass: '',
    nameRules: [
      v => !!v || 'Введите логин',
      v => (v && v.length >= 4)
    ],
    passRules: [
      v => (v && v.length >= 4)
    ]
  }),
  methods: {
    logIn () {
      this.$store.dispatch('logIn', {
        name: this.name,
        pass: this.pass
      })
      this.$emit('close', false)
    },
    reg () {
      this.$emit('reg')
    }
  }
}
</script>

<style>

</style>
