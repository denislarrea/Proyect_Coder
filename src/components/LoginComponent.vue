<template>
    <div>
      <b-container fluid>
        <b-row>
          <b-col></b-col>
          <b-col>
            <!-- login form -->
            <b-form v-if="show" @submit="onSubmit" @reset="onReset">
              <b-form-group
                id="input-group-1"
                label="Usuario"
                label-for="input-1"
                description="Nunca compartiremos tu E-mail"
              >
                <b-form-input
                  id="input-1"
                  v-model="form.email"
                  type="email"
                  placeholder="Ingresa tu E-mail"
                  required
                ></b-form-input>
              </b-form-group>
  
              <b-form-group
                id="input-group-2"
                label="Contraseña"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="form.pass"
                  placeholder="Ingresa tu Contraseña"
                  type="password"
                  required
                ></b-form-input>
              </b-form-group>
  
              <b-form-group id="select-group-3">
                <p>
                  Si todavia no te registrate... Hace click
                  <a href="#" v-on:click="changeForm">aquí.</a>
                </p>
              </b-form-group>
  
              <b-button type="submit" variant="primary">Ingresar</b-button>
              <b-button type="reset" variant="danger">Regresar</b-button>
            </b-form>
  
            <!-- Formulario de Registro -->
            <b-form v-else @submit="onSubmit" @reset="onReset">
              <b-form-group
                id="input-group-1"
                label="E-mail:"
                label-for="input-1"
                
              >
                <b-form-input
                  id="input-1"
                  v-model="form.email"
                  type="email"
                  placeholder="Sera utilizado como usuario"
                  required
                ></b-form-input>
              </b-form-group>
  
              <b-form-group
                id="input-group-2"
                label="Nombre"
                label-for="input-2"
              >
                <b-form-input
                  id="input-2"
                  v-model="form.name"
                  type="text"
                  placeholder="Ingresa tu Nombre"
                  required
                ></b-form-input>
              </b-form-group>
  
              <b-form-group
                id="input-group-3"
                label="Apellido"
                label-for="input-3"
              >
                <b-form-input
                  id="input-3"
                  v-model="form.surname"
                  type="text"
                  placeholder="Ingresa tu Apellido"
                  required
                ></b-form-input>
              </b-form-group>
  
              <b-form-group
                id="input-group-4"
                label="Contraseña"
                label-for="input-4"
                description="Debera contener Mayusc., Minusc. y Num."
              >
                <b-form-input
                  id="input-4"
                  v-model="form.pass"
                  placeholder="Ingresar contraseña"
                  type="password"
                  required
                ></b-form-input>
                
              </b-form-group>
  
              <b-form-group id="select-group-3">
                <p>
                  Si ya tenés una cuenta de registro Ingresá
                  <a href="#" v-on:click="changeForm">aquí.</a>
                </p>
              </b-form-group>
  
              <b-button type="submit" variant="primary">Ingresar</b-button>
              <b-button type="reset" variant="danger">Regresar</b-button>
            </b-form>
          </b-col>
          <b-col></b-col>
        </b-row>
      </b-container>
    </div>
  </template>
  
  <script>
  export default {
    name: "LoginComponent",
    data() {
      return {
        form: {
          name: "",
          surname: "",
          email: "",
          pass: "",
        },
        show: true,
      };
    },
    methods: {
      onSubmit(event) {
        event.preventDefault();
        console.log("usuario a loguear: ", JSON.stringify(this.form));
        this.$emit("logged", false);
      },
      onReset(event) {
        event.preventDefault();
  
        // Reset our form values
        this.form.name = "";
        this.form.surname = "";
        this.form.email = "";
        this.form.pass = "";
  
        // Trick to reset/clear native browser form validation state
        this.show = false;
        this.$nextTick(() => {
          this.show = true;
        });
      },
      changeForm() {
        this.show = !this.show;
      },
    },
  };
  </script>
  
  <style scoped>
  .cabecera {
    height: 80px;
  }
  
  form {
    color: antiquewhite;
    margin-top: 130px;
    margin-bottom: 70px;
  }
  
  button {
    margin-right: 1rem;
    margin-left: 1rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  </style>
  