<template>
  <v-app>
    <navBar/>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import navBar from './components/navBar.vue'

export default {
  name: 'App',
  components: {
    navBar
  },

  data: () => ({
    //
  }),
};
</script>
