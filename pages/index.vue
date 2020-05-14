<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-center">
        <!-- <logo /> -->
        <!-- <vuetify-logo /> -->
      </div>
      <v-card color="light-blue">
        <v-card-title>
        <!-- <v-card-title class="headline"> -->
          Sample Templates
        </v-card-title>
        <v-card-actions class="mb-12">
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/"
          >
            Home
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/api2"
          >
            API 2
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/api_rate1"
          >
            API 1
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/api3"
          >
            API 3
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/api4"
          >
            API 4
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/test_todo"
          >
            Testcases
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/test_dragdrop"
          >
            DragDrop
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_chart_google"
          >
            Chart G
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_todo"
          >
            Todo2
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_chart"
          >
            Chart
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/Login"
          >
            Login
          </v-btn>
        </v-card-actions>
        <v-card-actions class="mb-12">
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Inspire
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template"
          >
            Template
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_sandbox"
          >
            Sandbox
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_google"
          >
            Google
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_youtube"
          >
            YouTube
          </v-btn>
          <v-btn
            color="primary"
            nuxt
            to="/template_login"
          >
            Login
          </v-btn>
        </v-card-actions>
        <v-spacer />

        <v-card-title>
          Welcome to the Vuetify + Nuxt.js template
        </v-card-title>
        <v-card-text>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
          <p>
            For more information on Vuetify, check out the <a
              href="https://vuetifyjs.com"
              target="_blank"
            >
              documentation
            </a>.
          </p>
          <p>
            If you have questions, please join the official <a
              href="https://chat.vuetifyjs.com/"
              target="_blank"
              title="chat"
            >
              discord
            </a>.
          </p>
          <p>
            Find a bug? Report it on the github <a
              href="https://github.com/vuetifyjs/vuetify/issues"
              target="_blank"
              title="contribute"
            >
              issue board
            </a>.
          </p>
          <p>Thank you for developing with Vuetify and I look forward to bringing more exciting features in the future.</p>
          <div class="text-xs-right">
            <em><small>&mdash; John Leider</small></em>
          </div>
          <hr class="my-3">
          <a
            href="https://nuxtjs.org/"
            target="_blank"
          >
            Nuxt Documentation
          </a>
          <br>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
          >
            Nuxt GitHub
          </a>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    // Logo,
    // VuetifyLogo
  }
}
</script>
