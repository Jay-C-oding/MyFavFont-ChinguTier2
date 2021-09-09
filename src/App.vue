<template>
  <div>
    <my-header />
    <font-input />
    <button id="BackToTop" @click="scrollToTop">TOP</button>
    <footer>
      Coded by JaY | July. 2021 | Chingu Solo Project Tier 2
    </footer>
  </div>
</template>

<script>
import myHeader from "./components/myHeader.vue";
import fontInput from "./components/fontInput.vue";

export default {
  name: "App",
  components: {
    fontInput,
    myHeader,
  },
  methods: {
    scrollToTop: function() {
      window.scrollTo(0, 0);
    },
  },
};
</script>

<style>
html {
  font-size: 80%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 4rem;
  margin-right: 15%;
  margin-left: 15%;
}
#BackToTop {
  width: 4rem;
  height: 4rem;
  position: fixed;
  top: 80%;
  right: 5%;
  font-family: sans-serif;
  border: 1px solid darkslategrey;
  border-radius: 1.5rem;
  background-color: white;
  color: darkslategrey;
  font-size: 1.5rem;
  text-align: center;
  padding: 0;
}

#BackToTop:hover {
  border: 1px solid white;
  background-color: darkslategrey;
  color: white;
}

footer {
  font-family: sans-serif;
  font-weight: 100;
  text-align: center;
  font-size: 1.5rem;
  position: fixed;
  bottom: 0%;
  right: 0%;
  width: 100%;
  height: 4%;
  padding-top: 2vh;
  background-color: white;
}
</style>
