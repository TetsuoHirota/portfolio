<template>
  <div id="app">
    <b-navbar toggleable="sm" type="dark" variant="dark">
      <b-navbar-brand href="#">TETSUO HIROTA</b-navbar-brand>

      <b-navbar-toggle target="navbar-toggle-collapse">
        <template v-slot:default="{ expanded }">
          <b-icon v-if="expanded" icon="chevron-bar-up"></b-icon>
          <b-icon v-else icon="chevron-bar-down"></b-icon>
        </template>
      </b-navbar-toggle>

      <b-collapse id="navbar-toggle-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item href="#aboutMe">ABOUT ME</b-nav-item>
          <b-nav-item href="#myWork">MY WORK</b-nav-item>
          <b-nav-item href="#contact">CONTACT</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <router-view/>
    
  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: url('./assets/triangle-mosaic.png');
}
</style>
