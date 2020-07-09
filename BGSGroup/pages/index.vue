<template>
  <v-layout justify-center align-center>
    <v-flex xs12 sm8 md8>
      <v-card class="mt-16 elevation-12">
        <v-card-title class="pl-6 pt-6"><h1>Авторизация</h1></v-card-title>
       <v-form 
      class="pa-6"
      ref="form"
      v-model="valid"
      validation
    >
      <v-text-field
        v-model="login"
        :counter="20"
        :rules="loginRules"
        label="Login"
        required
      ></v-text-field>
  
      <v-text-field
        v-model="password"
        :rules="passwordRules"
        type="password"
        :counter="6"
        label="Password"
        required
      ></v-text-field>
       <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4"
        @click="validate"
        :to="{name: `profile-id`, params: {id: person.userId}}"
      >
        Validate
      </v-btn>
       </v-form>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>

export default {

  data() {
    return {
      valid: false,
      login: '',
      loginRules: [
        v => !!v || 'Login is required',
        v => (v && v.length <= 20) || 'Login must be less than 20 characters',
      ],
      password: '',
      passwordRules: [
        v => !!v || 'Password is required',
        v => (v && v.length >= 6) || "Login must be more than 6 characters"
      ],
      person: {   
        userId: 'logshoy'
      }
    }
  },
    methods: {
      validate () {
        this.$refs.form.validate()
      }
    }
}
</script>
