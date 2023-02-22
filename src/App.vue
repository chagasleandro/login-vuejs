<template>
  <v-app>
    <div class="background"></div>
    <v-main class="d-flex justify-center align-center">
      <v-col cols="10" lg="4" class="mx-auto">
        <v-card class="pa-4">
          <div class="text-center">
            <v-avatar size="100" color="indigo lighten-4">
              <v-icon size="40" color="indigo">
                mdi-account
              </v-icon>
            </v-avatar>
            <h2 class="indigo--text">Vue login page</h2>
          </div>
          <v-form @submit.prevent="submitHandler" ref="form">
            <v-card-text>
              <v-text-field
                  v-model="email"
                  :rules="emailRules" 
                type="email" 
                label="E-mail" 
                placeholder="Email"
                prepend-inner-icon="mdi-account" 
              />
              <v-text-field 
                v-model="password"
                :rules="passwordRules"
                :type="passwordShow? 'text' : 'password'" 
                label="Password" 
                placeholder="Password"
                prepend-inner-icon="mdi-key" 
                :append-icon="passwordShow ? 'mdi-eye': 'mdi-eye-off'"
                @click:append="passwordShow = !passwordShow"
                      required
              />
              <v-switch label="Remember me" color="indigo"></v-switch>
            </v-card-text>
            <v-card-actions class="justify-center">
              <v-btn :loading="loading" type="submit" color="indigo">
                <span class="white--text px-8">Login</span>  
              </v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-col>
    </v-main>
    <v-snackbar top color="green" v-model="snackbar">
      Login success
    </v-snackbar>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  data: () => ({
    loading: false,
    snackbar:false,
    passwordShow:false,
    password: '',
    passwordRules: [
      v => !!v || 'Name is required',
      v => (v && v.length <= 10) || 'Name must be less than 10 characters',
    ],
    email: '',
    emailRules: [
      v => !!v || 'E-mail is required',
      v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
  }),
  methods:{
    submitHandler(){
      if (this.$refs.form.validate()){
          this.loading = true
        setTimeout(()=> {
          this.loading = false
          this.snackbar = true
        },3000)
      }
    }
  }
};
</script>

<style>
  .background{
    background-image: url(./assets/Order-Banner.jpg) !important;
    height: 300px;
    width: 100%;
    display: flex;
    position: absolute;
    top: 0;
    background-size: cover;
  }
</style>
