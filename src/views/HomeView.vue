<template>
  <v-container grid-list-xl>
    <v-layout row wrap>
      <v-flex md6>
        <v-card
          v-for="(tarea, index) in listaTareas"
          :key="index"
          class="pa-md-4 mb-4"
        >
          <v-chip class="ma-2 ml-0" color="indigo" label text-color="white">
            <v-icon left> mdi-label </v-icon>
            {{ tarea.titulo }}
          </v-chip>
          <p>
            {{ tarea.descripcion }}
          </p>
          <v-btn @click="editarCuerpo(index)" color="warning">Editar</v-btn>
          <v-btn @click="eliminarTarea(tarea.id)" color="error" class="ms-3"
            >Eliminar</v-btn
          >
        </v-card>
      </v-flex>
      <v-flex md6 v-if="formAgregar">
        <v-card class="mb-3 pa-3">
          <v-form @submit.prevent="agregarTarea">
            <v-text-field
              v-model="titulo"
              label="Título de la tarea"
            ></v-text-field>
            <v-textarea
              v-model="descripcion"
              label="Descripción de la tarea"
            ></v-textarea>
            <v-btn block color="success" type="submit">Agregar Tarea</v-btn>
          </v-form>
        </v-card>
      </v-flex>

      <v-flex md6 v-if="!formAgregar">
        <v-card class="mb-3 pa-3">
          <v-form @submit.prevent="editarTarea">
            <v-text-field
              v-model="titulo"
              label="Título de la tarea"
            ></v-text-field>
            <v-textarea
              v-model="descripcion"
              label="Descripción de la tarea"
            ></v-textarea>
            <v-btn block color="warning" type="submit">Editar Tarea</v-btn>
          </v-form>
        </v-card>
      </v-flex>
    </v-layout>

    <v-snackbar v-model="snackbar" :multi-line="multiLine">
      {{ mensaje }}

      <template v-slot:action="{ attrs }">
        <v-btn color="red" text v-bind="attrs" @click="snackbar = false">
          Cerrar
        </v-btn>
      </template>
    </v-snackbar>
  </v-container>
</template>

<script>
import HelloWorld from "../components/HelloWorld";

export default {
  name: "Home",

  data() {
    return {
      listaTareas: [
        {
          id: 1,
          titulo: "Tarea 1",
          descripcion: "Hacer curso de udemy",
        },
        {
          id: 2,
          titulo: "Tarea 2",
          descripcion: "dormir mucho",
        },
      ],
      titulo: "",
      descripcion: "",
      multiLine: true,
      snackbar: false,
      mensaje: "",
      formAgregar: true,
    };
  },

  components: {
    HelloWorld,
  },

  methods: {
    agregarTarea() {
      if (this.titulo === "" || this.descripcion === "") {
        this.snackbar = true;
        this.mensaje = "¡Debes llenar todos los campos!";
      } else {
        this.listaTareas.push({
          id: Date.now(),
          titulo: this.titulo,
          descripcion: this.descripcion,
        });
        (this.titulo = ""), (this.descripcion = "");
        this.snackbar = true;
        this.mensaje = "Tarea agregada";
        localStorage.setItem("listaTareas", JSON.stringify(this.listaTareas));
      }
    },
    eliminarTarea(id) {
      this.listaTareas = this.listaTareas.filter(
        (elemento) => elemento.id != id
      );
      localStorage.setItem("listaTareas", JSON.stringify(this.listaTareas));
    },

    editarCuerpo(index) {
      this.formAgregar = false;
      this.titulo = this.listaTareas[index].titulo;
      this.descripcion = this.listaTareas[index].descripcion;
      this.indexTarea = index;
    },

    editarTarea() {
      this.listaTareas[this.indexTarea].titulo = this.titulo;
      this.listaTareas[this.indexTarea].descripcion = this.descripcion;
      this.formAgregar = true;
      this.titulo = "";
      this.descripcion = "";
      this.snackbar = true;
      this.mensaje = "Editaste la tarea";
      localStorage.setItem("listaTareas", JSON.stringify(this.listaTareas));
    },
  },
  created: function () {
    document.title = "Digicard | Práctica Vuetify"
    let datosLS = JSON.parse(localStorage.getItem("listaTareas"));
    if (datosLS === null) {
      this.listaTareas = [];
    } else {
      this.listaTareas = datosLS;
    }
  },
};
</script>
