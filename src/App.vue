<template>
  <v-app>
    <v-main class="gradientBackground">
      <v-container :class="containerClass">
        <v-card :elevation="8">
          <v-row class="grey lighten-2">
            <v-col cols="12"
                   sm="4"
                   class="grey darken-3 white--text pa-6"
            >
              <div class="text-center">
                <v-avatar :size="120" class="pa-12 text-center">
                  <img src="@/assets/img/CristianIncarnato.jpeg"/>
                </v-avatar>
                <h5 class="text-h4 font-weight-bold pt-2 ">{{ resume.name }} {{ resume.lastname }}</h5>
                <h6 class="
                  text-h5
                  font-weight-bold py-2
                  red--text text--lighten-1
                  ">
                  {{ resume.title }}
                </h6>
              </div>

              <!--INFO-->
              <h5 class="text-h5 mt-5">Info</h5>
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
              <h5 class="text-h5 mt-8">Idiomas</h5>
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
              <h5 class="text-h5 mt-8">Intereses</h5>
              <v-divider dark></v-divider>
              <v-chip-group column>
                <v-chip dark v-for="(item,i) in resume.interests" :key="i">
                  <v-icon left>{{ item.icon }}</v-icon>
                  <span>{{ item.value }}</span>
                </v-chip>
              </v-chip-group>

              <!--DESARROLLO-->
              <h5 class="text-h5 mt-8">Desarrollo</h5>
              <v-divider dark></v-divider>
              <ul class="mt-3">
                <li v-for="(item,i) in resume.development" :key="i">
                  {{ item }}
                </li>

              </ul>

              <!--NETWORKING-->
              <h5 class="text-h5 mt-8">Redes</h5>
              <v-divider dark></v-divider>
              <ul class="mt-3">
                <li v-for="(item,i) in resume.networking" :key="i">
                  {{ item }}
                </li>

              </ul>

              <!--TELEFONIA-->
              <h5 class="text-h5 mt-8">Telefonía</h5>
              <v-divider dark></v-divider>
              <ul class="mt-3">
                <li v-for="(item,i) in resume.telephony" :key="i">
                  {{ item }}
                </li>

              </ul>

              <!--MONITORIA & LOGS-->
              <h5 class="text-h5 mt-8">Monitoria & Logs</h5>
              <v-divider dark></v-divider>
              <ul class="mt-3">
                <li v-for="(item,i) in resume.monitoring" :key="i">
                  {{ item }}
                </li>

              </ul>

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
              <v-card class="mt-4">
                <v-card-title>Experiencia</v-card-title>
                <v-divider></v-divider>
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
                          <template v-if="Array.isArray(item.description)">
                            <div v-for="(d,i) in item.description" :key="i">
                              <h5 class="subtitle-1 font-weight-bold">{{ d.title }}</h5>
                              <p>{{ d.description }}</p>
                            </div>
                          </template>
                          <p v-else>{{ item.description }}</p>
                        </div>
                      </div>
                    </v-timeline-item>
                  </v-timeline>
                </v-card-text>

              </v-card>

              <!--LENGUAGES Y TECNOLOGIAS-->
              <card-gallery
                  title="Lenguajes de programación"
                  subtitle="Nivel de experiencia y conocimiento"
                  :items="resume.devLanguage"
              ></card-gallery>

              <!--Frameworks y Librerias-->
              <card-gallery
                  title="Frameworks y Librerías"
                  subtitle="Nivel de experiencia y conocimiento"
                  :items="resume.devFrameworks"
              ></card-gallery>

              <!--ORM & ODM-->
              <card-gallery
                  title="ORM & ODM"
                  subtitle="Nivel de experiencia y conocimiento"
                  :items="resume.devOrmOdm"
              ></card-gallery>


            </v-col>
          </v-row>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>

import CardGallery from "@/components/CardGallery/CardGallery";

export default {
  name: 'App',

  components: {CardGallery},
  computed: {
    containerClass() {
      if (this.$vuetify.breakpoint.smAndUp) {
        return 'py-6'
      } else {
        return 'pa-0 ma-0'
      }
    }
  },
  data: () => ({
    levels: [
      'Básico',
      'Intermedio',
      'Avanzado'
    ],
    resume: {
      name: 'Cristian',
      lastname: 'Incarnato',
      title: 'Full stack developer',
      devOrmOdm: [
        {
          title: 'Mongoose',
          level: 3,
          img: require('@/assets/tech/mongoose.png'),
        },
        {
          title: 'Doctrine',
          level: 3,
          img: require('@/assets/tech/doctrine.png'),
        },
        {
          title: 'Sequelize',
          level: 2,
          img: require('@/assets/tech/sequelize.png'),
        },
        {
          title: 'Hibernate',
          level: 2,
          img: require('@/assets/tech/hibernate.png'),
        },
        {
          title: 'Eloquent',
          level: 1,
          img: require('@/assets/tech/eloquent.png'),
        },
      ],
      devFrameworks: [
        {
          title: 'Vuejs',
          level: 3,
          img: require('@/assets/tech/vuejs.jpg'),
        },
        {
          title: 'Vuetify',
          level: 3,
          img: require('@/assets/tech/vuetifyy.png'),
        },
        {
          title: 'Angularjs',
          level: 2,
          img: require('@/assets/tech/angular.png'),
        },
        {
          title: 'React',
          level: 2,
          img: require('@/assets/tech/react.png'),
        },
        {
          title: 'jQuery',
          level: 2,
          img: require('@/assets/tech/jquery.png'),
        },


        {
          title: 'Express',
          level: 3,
          img: require('@/assets/tech/express.png'),
        },
        {
          title: 'Apollo',
          level: 3,
          img: require('@/assets/tech/apollo.png'),
        },
        {
          title: 'Spring',
          level: 2,
          img: require('@/assets/tech/spring.png'),
        },
        {
          title: 'Zend',
          level: 3,
          img: require('@/assets/tech/zf.png'),
        },
        {
          title: 'Laravel',
          level: 2,
          img: require('@/assets/tech/laravel2.png'),
        },
        {
          title: 'Grails',
          level: 2,
          img: require('@/assets/tech/grails.jpg'),
        },
        {
          title: 'Django',
          level: 1,
          img: require('@/assets/tech/django.png'),
        },
        {
          title: 'Rails',
          level: 1,
          img: require('@/assets/tech/rails.png'),
        },
      ],
      devLanguage: [
        {
          title: 'Javascript',
          level: 3,
          img: require('@/assets/tech/javascript.png'),
        },
        {
          title: 'PHP',
          level: 3,
          img: require('@/assets/tech/php.png'),
        },
        {
          title: 'Java',
          level: 2,
          img: require('@/assets/tech/java.png'),
        },
        {
          title: 'Groovy',
          level: 2,
          img: require('@/assets/tech/groovy.png'),
        },
        {
          title: 'Python',
          level: 1,
          img: require('@/assets/tech/python.png'),
        },
        {
          title: 'Ruby',
          level: 1,
          img: require('@/assets/tech/ruby.png'),
        },
      ],
      experience: [
        {
          date: '2015-Actualidad',
          title: 'Sondeos',
          subtitle: 'Líder IT',
          description: [
            {
              title: 'Desarrollo de Software',
              description: 'Liderazgo en desarrollo de software. Metodología Scrum. Lenguajes Javascript, Java, PHP, Python, Ruby, Groovy. Frameworks Spring, Zend, Laravel, Grails, Express, Vuejs, React, Angular, Nuxt. Integración y delivery continuo.'
            },
            {
              title: 'Infraestructura y Tecnología',
              description: 'Gestión de infraestructura. Servidores, sistemas operativos, virtualización, docker, redes, firewalls, bases de datos SQL y NOSQL, alta disponibilidad, balanceo.'
            }
          ]
        },
        {
          date: '2013-2015',
          title: 'IPLAN',
          subtitle: 'Jefe de NOC',
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
          value: 'Poadcast'
        },
        {
          icon: 'mdi-dog',
          value: 'Dachshund'
        },
        {
          icon: 'mdi-link-lock',
          value: 'Blockchain'
        },
        {
          icon: 'mdi-currency-btc',
          value: 'Cryptomoendas'
        },
      ],
      extract: [
        'Me destaco como desarrollador full stack y cuento con un gran complemento de conocimientos de IT en general. Mi paso por telecomunicaciones me permitió adquirir gran experiencia en redes y telefonía.',
        'Tengo un perfil dinámico que me permite desempeñarme en diferentes roles, pudiendo contribuir en diferentes etapas y contextos de un proyecto.',
        'Disfruto de enseñar y compartir conocimientos. He liderado y formado equipos. Soy conciliador y perseverante. Siempre intento con el ejemplo.',
      ],
      development: [
        'Programación Orientada a Objetos. Patrones de Diseño.',
        'Metodologías ágiles',
        'TDD (Test Driven Development)',
        'Test Unitario/Integración',
        'Manejo de Hilos',
        'Manejo de Excepciones',
        'Volumen de datos',
        'API REST',
        'GraphQL',
        'Programación funcional',
        'Programación asíncrona',
        'DB SQL & NOSQL',
        'CI/CD',
        'Docker',
        'User story'
      ],
      networking: [
        'TCP/IP',
        'Firewalling',
        'Routing',
        'Switching',
        'VPN',
        'Wireshark'

      ],
      telephony: [
        'Voip, SIP, RTP',
        'Tramas E1',
        'Centrales telefónicas',

      ],
      monitoring: [
        'Zabbix',
        'Datadog',
        'Tivoli',
        'Nagios',
        'Cacti',
        'Syslog',
        'Kibana+Elastic'

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

.whiteShadow {
  text-shadow: rgba(255, 255, 255, 0) -1px 0, rgba(255, 255, 255, 0) 0 -1px,
  rgba(255, 255, 255, 0.7) 1px 0, rgba(255, 255, 255, 0.7) 0 1px,
  rgba(255, 255, 255, 0.2) -1px -1px, rgba(255, 255, 255, 0.2) 1px 1px;
}
</style>
