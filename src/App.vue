<template>
  <div>
    <Sidebar id="sidebar"/>
    <NavBar id="navbar"/>
    <MainPage id="main-page"/>
  </div>
</template>

<script>
import Sidebar from './components/Sidebar.vue';
import NavBar from './components/NavBar.vue';
import MainPage from './components/MainPage.vue'

export default {
  components: {
    Sidebar,
    NavBar,
    MainPage,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Abel&family=Oswald:wght@200..700&display=swap');

body {
    font-family: "Oswald", sans-serif;
    background-color: #F8F6F4;
}

#sidebar {
  width: 12%;
  height: 100vh;
  position:fixed;
  border-right: solid grey 2px;
  box-shadow: 10px 3px 5px 0px grey;
  background-color: #cfcfcb;
}

#navbar {
  margin-left: 14%;
  padding-top: 2%;
  position: fixed;
  top: 0;
  left: 0;
  width: 85%;
  background-color: #F8F6F4;
  max-width: 1950px;
}

#main-page{
  padding-left: 14%;
  padding-top: 270px;
  max-width: 1950px;
}

</style>
