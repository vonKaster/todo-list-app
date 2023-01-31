<template>
  <v-card color="blue lighten-4" flat tile>
    <v-toolbar dense>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Digicard | Vuetify</v-toolbar-title>
      <v-btn :to="{name: 'home'}" depressed outlined color="indigo" class="ms-4"> Home </v-btn>
      <v-btn :to="{name: 'grid'}" depressed outlined color="indigo" class="ms-4"> Grid </v-btn>
      <v-btn :to="{name: 'botones'}" depressed outlined color="indigo" class="ms-4"> Botones </v-btn>
      <v-btn :to="{name: 'cards'}" depressed outlined color="indigo" class="ms-4"> Cards </v-btn>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
  </v-card>
</template>

<script>
export default {

  name: "navBar",
  data() {
    return {};
  },
};
</script>
