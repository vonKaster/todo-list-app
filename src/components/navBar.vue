<template>
  <div>
    <v-app-bar app fixed color="#DFE0E2" dark>
      <v-toolbar-title>
        <img
          class="mt-2 logo-pokedex"
          :src="require('../assets/logodigicard.png')"
        />
      </v-toolbar-title>  
      <v-spacer />
      <v-btn :to="{name: 'home'}" depressed outlined color="indigo" class="ms-4"> Home </v-btn>
      <v-btn :to="{name: 'grid'}" depressed outlined color="indigo" class="ms-4"> Grid </v-btn>
      <v-btn :to="{name: 'botones'}" depressed outlined color="indigo" class="ms-4"> Botones </v-btn>
      <v-btn :to="{name: 'cards'}" depressed outlined color="indigo" class="ms-4"> Cards </v-btn>
    </v-app-bar>
  </div>
</template>

<script>  
export default {
  name: "navBar",
  data() {
    return {
    };
  },
};
</script>