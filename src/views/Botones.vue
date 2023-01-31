<template>
  <div class="container">
    <v-row class="mt-4" justify="space-around">
      <v-btn depressed> Color Normal </v-btn>
      <v-btn depressed color="primary"> Color Primario </v-btn>
      <v-btn depressed color="error"> Color Error Error </v-btn>
      <v-btn depressed disabled> Deshabilitado </v-btn>
    </v-row>

    <v-row class="mt-10" justify="space-around">
      <v-btn class="mx-2" fab dark small color="primary">
        <v-icon dark> mdi-minus </v-icon>
      </v-btn>

      <v-btn class="mx-2" fab dark small color="pink">
        <v-icon dark> mdi-heart </v-icon>
      </v-btn>

      <v-btn class="mx-2" fab dark color="indigo">
        <v-icon dark> mdi-plus </v-icon>
      </v-btn>

      <v-btn class="mx-2" fab dark color="teal">
        <v-icon dark> mdi-format-list-bulleted-square </v-icon>
      </v-btn>

      <v-btn class="mx-2" fab dark large color="cyan">
        <v-icon dark> mdi-pencil </v-icon>
      </v-btn>

      <v-btn class="mx-2" fab dark large color="purple">
        <v-icon dark> mdi-android </v-icon>
      </v-btn>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p>Normal</p>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon color="pink">
          <v-icon>mdi-heart</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon color="indigo">
          <v-icon>mdi-star</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon color="green">
          <v-icon>mdi-cached</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon color="deep-orange">
          <v-icon>mdi-thumb-up</v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <v-row class="mt-12">
      <v-col cols="12">
        <p>Disabled</p>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon disabled>
          <v-icon>mdi-heart</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon disabled>
          <v-icon>mdi-star</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon disabled>
          <v-icon>mdi-cached</v-icon>
        </v-btn>
      </v-col>

      <v-col cols="12" sm="3">
        <v-btn icon disabled>
          <v-icon>mdi-thumb-up</v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <div class="text-center">
      <v-btn
        class="ma-2"
        :loading="loading"
        :disabled="loading"
        color="secondary"
        @click="loader = 'loading'"
      >
        Aceptar términos
      </v-btn>

      <v-btn
        :loading="loading3"
        :disabled="loading3"
        color="blue-grey"
        class="ma-2 white--text"
        @click="loader = 'loading3'"
      >
        Subir
        <v-icon right dark> mdi-cloud-upload </v-icon>
      </v-btn>

      <v-btn
        class="ma-2"
        :loading="loading2"
        :disabled="loading2"
        color="success"
        @click="loader = 'loading2'"
      >
        Loader Custom
        <template v-slot:loader>
          <span>Cargando...</span>
        </template>
      </v-btn>

      <v-btn
        class="ma-2"
        :loading="loading4"
        :disabled="loading4"
        color="info"
        @click="loader = 'loading4'"
      >
        Loader con Icono
        <template v-slot:loader>
          <span class="custom-loader">
            <v-icon light>mdi-cached</v-icon>
          </span>
        </template>
      </v-btn>

      <v-btn
        :loading="loading5"
        :disabled="loading5"
        color="blue-grey"
        class="ma-2 white--text"
        fab
        @click="loader = 'loading5'"
      >
        <v-icon dark> mdi-cloud-upload </v-icon>
      </v-btn>
    </div>

    <div class="text-center">
      <v-btn class="ma-2" outlined color="indigo"> Botón outlined </v-btn>
      <v-btn class="ma-2" outlined fab color="teal">
        <v-icon>mdi-format-list-bulleted-square</v-icon>
      </v-btn>
      <v-btn class="ma-2" outlined large fab color="indigo">
        <v-icon>mdi-pencil</v-icon>
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  name: "botones",
  data() {
    return {
      loader: null,
      loading: false,
      loading2: false,
      loading3: false,
      loading4: false,
      loading5: false,
    };
  },
  watch: {
    loader() {
      const l = this.loader;
      this[l] = !this[l];

      setTimeout(() => (this[l] = false), 3000);

      this.loader = null;
    },
  },
};
</script>

<style>
  .custom-loader {
    animation: loader 1s infinite;
    display: flex;
  }
  @-moz-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-webkit-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @-o-keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
  @keyframes loader {
    from {
      transform: rotate(0);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>
