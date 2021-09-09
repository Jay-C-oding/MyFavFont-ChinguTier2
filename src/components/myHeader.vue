<template>
  <header>
    <div class="menu">
      <div class="menuIcon">CATALOG</div>
      <div class="menuIcon">FEATURED</div>
      <div class="menuIcon">ARTICLES</div>
      <div class="menuIcon">ABOUT</div>
    </div>
  </header>
</template>

<script>
export default {
  name: "myHeader",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  border-bottom: 2px solid darkslategrey;
  display: grid;
  grid-template-columns: repeat(4 20%);
  gap: 0px 0px;
  grid-template-areas: "logo . menu menu";
  max-height: 7vh;
}
.menu {
  color: darkslategray;
  font-family: sans-serif;
  grid-area: menu;
  display: flex;
  justify-content: space-between;
}
.menuIcon {
  display: inline-block;
  font-weight: 100;
  vertical-align: middle;
  position: relative;
  font-size: 15px;
}
</style>
