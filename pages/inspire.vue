<template>
  <v-layout>
    <v-flex class="text-center">
      <img
        src="/v.png"
        alt="Vuetify.js"
        class="mb-5"
      >
      <blockquote class="blockquote">
        &#8220;First, solve the problem. Then, write the code.&#8221;
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
          </small>
        </footer>
      </blockquote>
      <v-card-actions>
        <v-btn
          color="primary"
          nuxt
          to="/"
        >
          Home page
        </v-btn>
      </v-card-actions>
    </v-flex>
  </v-layout>
</template>
