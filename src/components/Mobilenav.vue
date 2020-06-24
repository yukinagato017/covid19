<template>
  <div class="mobileNav">
    <button @click="slideNav = true">
      <vue-fontawesome icon="bars" size="3" color="lightgray"></vue-fontawesome>
    </button>
    <div v-if="slideNav" class="slideNav" id="slide">
      <button @click="slideNav = false">
        <vue-fontawesome
          icon="times-circle"
          size="3"
          color="black"
          margin="10"
          float="right"
        ></vue-fontawesome>
      </button>
      <a href="/">Home</a>
      <a href="/about">About</a>
    </div>
  </div>
</template>
<script>
export default {
  name: "Mobilenav",
  data() {
    return {
      slideNav: false
    };
  },
  methods: {}
};
</script>
<style lang="scss" scoped>
.mobileNav {
  margin: 9px 0px 5px 11px;
  cursor: pointer;
}
.slideNav {
  background-color: white;
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 1;
  left: 0px;
  top: 0px;
  animation-duration: 1s;
  animation-name: slidein;

  @keyframes slidein {
    from {
      margin-right: 0%;
      width: 300%;
    }

    to {
      margin-right: 100%;
      width: 100%;
    }
  }

  a {
    font-weight: bold;
    color: #000;
    margin: 40px;
    text-decoration: none;
    text-align: center;
    font-size: 3em;
    display: block;

    &.router-link-exact-active {
      color: #f39c12;
    }
  }
}
button {
  border: none;
  background: none;
  cursor: pointer;
  outline-style: none;
}
</style>
