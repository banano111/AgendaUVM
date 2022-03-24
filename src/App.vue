<script>
export default {
  data() {
    return {
      nombre: "",
      telefono: "",
      email: "",
      contactos: []
    };
  },
  methods: {
    LimpiarInput(){
      this.nombre = "";
      this.telefono = "";
      this.email = "";
    },

    AgregarUsuario() {
      var usuario = {
        nombre: this.nombre,
        telefono: this.telefono,
        email: this.email
      }
      this.contactos.push(usuario)
      this.LimpiarInput()
    }
  },
};
</script>

<template>
  <nav>
    <div class="nav-wrapper">
      <a href="#" class="brand-logo margen-logo">Agenda UVM</a>
    </div>
  </nav>

  <div class="container" id="principal">
    <div class="row">
      <div class="col s4 white z-depth-2">
        <form @submit.prevent="AgregarUsuario">
          <div class="row">
            <div class="input-field col s12">
              <i class="material-icons prefix">account_circle</i>
              <input v-model="nombre" id="name" type="text" class="validate" />
              <label for="name">Nombre Completo</label>
            </div>
            <div class="input-field col s12">
              <i class="material-icons prefix">phone</i>
              <input
                v-model="telefono"
                id="telephone"
                type="tel"
                class="validate"
              />
              <label for="telephone">Telefono</label>
            </div>
            <div class="input-field col s12">
              <i class="material-icons prefix">email</i>
              <input v-model="email" id="email" type="email" class="validate" />
              <label for="email">Correo</label>
            </div>
            <button
              class="btn waves-effect waves-light botonCentrado"
              type="submit"
              name="action"
            >
              Agregar Contacto
              <i class="material-icons right">send</i>
            </button>
          </div>
        </form>
      </div>
      <div class="col s6 white z-depth-2 margen-izquierdo">
        <table class="stripped">
          <thead>
            <tr>
              <th>Nombre</th>
              <th>Telefono</th>
              <th>Correo</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="contacto in contactos" :key="contacto.email">
              <td>{{contacto.nombre}}</td>
              <td>{{contacto.telefono}}</td>
              <td>{{contacto.email}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<style>
#principal {
  margin-top: 5%;
}

.margen-izquierdo {
  margin-left: 10% !important;
}

.margen-logo {
  margin-left: 2% !important;
}

.botonCentrado{
  margin-top: 5%;
  margin-left: 15% !important;
}
</style>
