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
        </v-card>
      </v-col>
    </v-main>
  </v-app>
</template>

<script>


export default {
  name: 'App',

  components: {
    
  },

  data: () => ({
    //
  }),
};
</script>

<style>
  .background{
    background-image: url(./assets/login.svg) !important;
    height: 300px;
    width: 100%;
    display: flex;
    position: absolute;
    top: 0;
    background-size: cover;
  }
</style>
