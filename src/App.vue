<template>
  
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark px-4">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <li class="nav-item active" v-for="(data, index) in menu" :key="index">
        <a class="nav-link" :href="data.link"> {{ data.label }}</a>
      </li>
    </ul>
    
  </div>
</nav>

  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld />
  <AboutUs />
  <SignIn />
  <!-- <ConTact /> -->
  <FooTer> </FooTer>
</template>


<script>

import HelloWorld from './components/HelloWorld.vue'
import FooTer from './components/FooTer.vue'
import AboutUs from './components/AboutUs.vue'
import SignIn from './components/SignIn.vue';
// import ConTact from './components/ConTact.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    AboutUs,
    SignIn,
    // ConTact,
    FooTer
  },
  data (){
    return {
      menu:[
      {
        label:"Home",
        link:"/home"
      },
      {
        label:"About us",
        link:"/AboutUs"
      },
      {
        label:"Contact",
        link:"/ContactUs"
      },
      {
        label:"Privacy Policy",
        link:"/PrivacyPolicy"
      }
      ]
    }
  }
}
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
