<template>
    <div>
      <b-navbar class="navbar navbar-expand-lg fixed-top navbar-scroll">
        <div class="container-fluid">
          <b-navbar-brand href="#" @click="backToHome" >Denis Bike-Shop</b-navbar-brand >
  
          <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
  
          <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav>
                <b-nav-item href="#">Accesorios</b-nav-item>
                <b-nav-item href="#">Service de Bicicleta</b-nav-item>
                <b-nav-item href="#" >Contactenos</b-nav-item>

            </b-navbar-nav>
  
            <b-navbar-nav class="ml-auto">

             <!-- <b-button class="nav-btn" @click="submitLogin">
                <b-icon icon="person-circle" class="nav-icon"></b-icon>
              </b-button>
              -->
                          <b-button class="nav-btn" @click="goToLogin">
              <b-icon
                v-if="logged"
                icon="emoji-laughing"
                class="nav-icon"
              ></b-icon>
              <b-icon v-else icon="person-circle" class="nav-icon"></b-icon>
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
    cartQ: {
      Number,
    },
    logged: {
      Boolean,
      required: true,
    },
  },
  methods: {
    goToLogin() {
      this.$emit("goToLogin", true);
    },
    backToHome() {
      this.$emit("backHome");
    },
  },
};
</script>
  
  <style scoped>
.navbar {
  width: 100%;
  min-width: 20rem;
  min-height: 4rem;
  z-index: 9;
  color: crimson;
  background: rgba(129, 151, 249, 0.676);
  backdrop-filter: blur(5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
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
  background-color: orange;
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
