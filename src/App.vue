<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>
    <div id="mobileNav"><Mobilenav /></div>
    <router-view />
  </div>
</template>
<script>
import Mobilenav from "@/components/Mobilenav.vue";
export default {
  components: {
    Mobilenav
  },
  data() {
    return {
      nav: true
    };
  }
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@300&display=swap");
$mobile: 700px;
#app {
  font-family: "Roboto Condensed", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
body {
  margin: 0px !important;
}
#nav {
  padding: 25px;
  background-color: #fff;
  a {
    font-weight: bold;
    color: #000;
    margin: 40px;
    text-decoration: none;

    &.router-link-exact-active {
      color: #f39c12;
    }
  }
}
#mobileNav {
  display: none;
}
@media screen and (max-width: $mobile) {
  #nav {
    display: none;
  }
  #mobileNav {
    display: block;
  }
}
</style>
