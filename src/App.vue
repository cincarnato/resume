<template>
  <v-app>
    <v-main class="gradientBackground">
      <v-container class="py-6">
        <v-card :elevation="8" class="grey lighten-2">
          <v-card-text class="pl-0 pt-0 pb-0">
            <v-row>
              <v-col cols="12"
                     sm="4"
                     class="grey darken-3 white--text "
              >
                <div class="text-center">
                  <v-avatar :size="120" class="pa-12 text-center">
                    <img src="@/assets/img/CristianIncarnato.jpeg"/>
                  </v-avatar>
                  <h5 class="text-h5 font-weight-bold pt-2 ">{{ resume.name }} {{ resume.lastname }}</h5>
                  <h6 class="subtitle-1 py-2 ">{{ resume.title }}</h6>
                </div>

                <!--INFO-->
                <h5 class="text-h5">Info</h5>
                <v-divider dark></v-divider>
                <v-list color="grey darken-3" dark>

                  <v-list-item v-for="(item,i) in resume.info" :key="i">
                    <v-list-item-icon>
                      <v-icon>{{ item.icon }}</v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <v-list-item-title>{{ item.value }}</v-list-item-title>
                      <v-list-item-subtitle>{{ item.label }}</v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>

                </v-list>

                <!--LANGUAGE-->
                <h5 class="text-h5">Idiomas</h5>
                <v-divider dark></v-divider>
                <v-list color="grey darken-3" dark>

                  <v-list-item v-for="(item,i) in resume.language" :key="i">
                    <v-list-item-content>
                      <v-list-item-title>{{ item.value }}</v-list-item-title>
                      <v-list-item-subtitle>{{ item.label }}</v-list-item-subtitle>
                    </v-list-item-content>
                  </v-list-item>

                </v-list>

                <!--INTERESTS-->
                <h5 class="text-h5">Intereses</h5>
                <v-divider dark></v-divider>
                <v-chip-group column>
                  <v-chip dark v-for="(item,i) in resume.interests" :key="i">
                    <v-icon left>{{ item.icon }}</v-icon>
                    <span>{{ item.value }}</span>
                  </v-chip>
                </v-chip-group>


              </v-col>
              <v-col cols="12" sm="8">
                <v-card>
                  <v-card-title>Extracto</v-card-title>
                  <v-divider></v-divider>
                  <v-card-text>
                    <p v-for="(t,i) in resume.extract" :key="i">{{ t }}</p>
                  </v-card-text>
                </v-card>

                <!--EXPERIENCE-->
                <v-card class="mt-3">
                  <v-card-text>

                    <v-timeline>
                      <v-timeline-item
                          v-for="(item, i) in resume.experience"
                          :key="i"
                          small
                      >
                        <template v-slot:opposite>
                        <span
                            class="subtitle-1 font-weight-bold"
                            v-text="item.date"
                        ></span>
                        </template>

                        <div class="py-4">
                          <h2 class="headline font-weight-light mb-2">
                            <b>{{ item.title }}</b> - {{ item.subtitle }}
                          </h2>
                          <div>
                            <p>{{ item.description }}</p>
                          </div>
                        </div>
                      </v-timeline-item>
                    </v-timeline>
                  </v-card-text>

                </v-card>

              </v-col>
            </v-row>
          </v-card-text>
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
      title: 'Extraordinary full stack developer',
      experience: [
        {
          date: '2013-2015',
          title: 'IPLAN',
          subtitle: 'Jefe NOC',
          description: "Liderar y organizar el equipo de operaciones 7 x 24. Definición de objetivos. Formación de Operadores. Mantenimiento y evolución de herramientas desarrolladas."
        },
        {
          date: '2010-2013',
          title: 'IPLAN',
          subtitle: 'Desarrollador',
          description: "Programación de herramientas para gestión de tareas, automatización,  detección de errores, control de calidad, coordinación de agenda."
        },
        {
          date: '2008-2010',
          title: 'IPLAN',
          subtitle: 'Operador NOC',
          description: "Configuración, mantenimiento, monitoria, resolución de incidentes sobre la red de internet y telefonía de IPLAN."
        }
      ],
      info: [
        {
          icon: 'mdi-email',
          label: 'Email',
          value: 'cristian.cdi@gmail.com'
        },
        {
          icon: 'mdi-flag',
          label: 'Nacionalidad',
          value: 'Argentina'
        },
        {
          icon: 'mdi-calendar',
          label: 'Nacimiento',
          value: '17 Enero 1985'
        },
      ],
      language: [
        {
          label: 'Ingles',
          value: 'Avanzado'
        },
      ],
      interests: [
        {
          icon: 'mdi-bike',
          value: 'Ciclismo'
        },
        {
          icon: 'mdi-nature',
          value: 'Naturaleza'
        },
        {
          icon: 'mdi-book',
          value: 'Libros'
        },
        {
          icon: 'mdi-teach',
          value: 'Enseñar'
        },
        {
          icon: 'mdi-desktop-classic',
          value: 'Informatica'
        },
        {
          icon: 'mdi-music',
          value: 'Música'
        },
        {
          icon: 'mdi-dog',
          value: 'Mascotas'
        },
        {
          icon: 'mdi-theater',
          value: 'Cine'
        },
      ],
      extract: [
        'Me destaco como desarrollador full stack y cuento con un gran complemento de conocimientos de IT en general. Mi paso por telecomunicaciones me permitió adquirir gran experiencia en redes y telefonía.',
        'Tengo un perfil dinámico que me permite desempeñarme en diferentes roles, pudiendo contribuir en diferentes etapas y contextos de un proyecto.',
        'Disfruto de enseñar y compartir conocimientos. He liderado y formado equipos. Soy conciliador y perseverante. Siempre intento con el ejemplo.',
      ]
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
