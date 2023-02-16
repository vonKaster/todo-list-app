<template>
    <v-footer color="primary lighten-1" padless>
      <v-row justify="center" no-gutters>
        <a target="_blank" v-for="link in links" :key="link.text" :href="link.href">
          <v-btn color="white" text rounded class="my-2">
            {{ link.text }}
          </v-btn>
        </a>
        <v-col class="primary lighten-1 py-4 text-center white--text" cols="12">
          {{ new Date().getFullYear() }} — <strong>Digicard</strong>
        </v-col>
      </v-row>
    </v-footer>
  </template>
  <script>
  export default {
    data: () => ({
      links: [
        { text: 'Home', href: 'https://fcaminos-digicard.netlify.app/index.html' },
        { text: 'Pokedex', href: 'https://fcaminos-pokedex-digicard.netlify.app/' },
        { text: 'Calendario', href: 'https://fcaminos-calendario-axios-vuetify.netlify.app/' },
        { text: 'Contacto', href: 'https://github.com/vonKaster' }
      ]
    })
  }
  </script>

  <style>

    a {
        text-decoration: none;
    }

  </style>