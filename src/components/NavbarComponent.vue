<template>
    <div>
      <b-navbar class="navbar navbar-expand-lg fixed-top navbar-scroll">
        <div class="container-fluid">
          <b-navbar-brand href="#" @click="backToHome" class="navbar-titlle">Denis Bike-Shop</b-navbar-brand >
  
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
  
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
                <b-nav-item href="#">Accesorios</b-nav-item>
                <b-nav-item href="#">Service de Bicicleta</b-nav-item>
                <b-nav-item href="#" >Contactenos</b-nav-item>

            </b-navbar-nav>
  
            <b-navbar-nav class="ml-auto">

              <b-button class="nav-btn" @click="submitLogin">
                <b-icon icon="person-circle" class="nav-icon"></b-icon>
              </b-button>
  
              <b-button v-b-toggle.sidebar-cart class="nav-btn">
                <b-icon icon="cart" class="nav-icon"></b-icon>
                <div v-if="cartQ > 0" class="cart-dot">
                  <p class="cart-total">{{ cartQ }}</p>
                </div>
              </b-button>
            </b-navbar-nav>
          </b-collapse>
        </div>
      </b-navbar>
    </div>
  </template>
  
  <script>
  export default {
    name: "NavbarComponent",
    components: {},
    props: {
      cartQ: Number,
    },
    methods: {
      submitLogin() {
        this.$emit("login", true);
      },
      backToHome() {
        this.$emit("login", false);
      },
    },
  };
  </script>
  
  <style scoped>
  .navbar {
    width: 100%;
    min-width: 25rem;
    min-height: 5rem;
    z-index: 12;
    color: crimson;
    text-decoration: none;
    background: rgba(108, 189, 236, 0.676);
    backdrop-filter: blur(5px);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    
  }

  .navbartitlle{

    text-decoration:dashed;
    size: 2rem;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;

  }
  
  .navbar-scrolled .nav-link,
  .navbar-scrolled .navbar-toggler .fa-bars {
    background: rgba(241, 241, 241, 0.676);
  }
  
  .navbar-light .navbar-brand {
    color: crimson;
  }
  
  .nav-icon {
    color: white;
   
 
  }
  
  button {
    border-radius: 50%;
    margin-left: 0.5rem;
    background-color: crimson;
    border-color: crimson;
    padding: 13px;
  }
  
  .button-content {
    border-radius: 50%;
    margin-left: 1rem;
    background-color: crimson;
    border-color: crimson;
  }
  
  .cart-dot {
    height: 1.8rem;
    width: 1.8rem;
    background-color: rgb(20, 194, 29);
    border-radius: 50%;
    z-index: 3;
    position: absolute;
    bottom: 1.8rem;
    right: 0.4rem;
  }
  
  .cart-total {
    color: #fff;
    font-size: 1rem;
    text-align: center;
    margin-top: 2px;
  }
  </style>
  