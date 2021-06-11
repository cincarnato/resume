<template>
  <v-app>
    <v-main class="gradientBackground">
      <v-container class="py-6">
        <v-card :elevation="8">
          <v-row>
            <v-col cols="12"
                   sm="4"
                   class="grey darken-3 white--text text-center"
            >
              <v-avatar :size="120" class="pa-12" >
                <img src="@/assets/img/CristianIncarnato.jpeg"/>
              </v-avatar>
              <h5 class="text-h5 font-weight-bold pt-2 ">{{resume.name}} {{resume.lastname}}</h5>
              <h6 class="subtitle-1 py-2 ">{{resume.title}}</h6>
            </v-col>
            <v-col cols="12" sm="8">

            </v-col>
          </v-row>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {},

  data: () => ({
    resume: {
      name: 'Cristian',
      lastname: 'Incarnato',
      title: 'Extraordinary full stack developer'
    }
  }),
};
</script>

<style>
.gradientBackground {
  background: #3A1C71;
  background: -webkit-linear-gradient(to right, #FFAF7B, #D76D77, #3A1C71);
  background: linear-gradient(to right, #FFAF7B, #D76D77, #3A1C71);
}
</style>
