<template>
  <div class="app">
    <!-- <div class="nav">
      <router-link to="/" >spacer</router-link>
      <router-link to="/about" >about</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<style lang="scss">
  * {
    box-sizing: border-box;
    font-family: fantasy;
    font-size: 10px;
    color: #fff;
  }
  body {
    margin: 0;
    padding: 0;
  }
</style>
