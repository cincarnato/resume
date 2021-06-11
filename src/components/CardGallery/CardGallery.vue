<template>
  <v-card class="mt-4">
    <v-card-title>{{title}}</v-card-title>
    <v-card-subtitle>{{subtitle}}</v-card-subtitle>
    <v-card-text class="pb-6">
      <v-row>
        <v-col
            cols="12" sm="6" md="4"
            class="mt-3"
            v-for="(dl,i) in items"
            :key="i"
        >

          <v-card>
            <v-row no-gutters align="center">
              <v-col cols="4" class="pa-3">
                <v-img contain :src="dl.img"></v-img>
              </v-col>
              <v-col cols="8">
                <v-card-title>{{ dl.title }}</v-card-title>
                <v-card-subtitle>{{ levels[dl.level - 1] }}</v-card-subtitle>
              </v-col>
            </v-row>
          </v-card>

        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "CardGallery",
  props: {
    title: String,
    subtitle: String,
    items: Array
  },
  data: () => ({
    levels: [
      'Básico',
      'Intermedio',
      'Avanzado'
    ],
  })
}
</script>

<style scoped>

</style>
