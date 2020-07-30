<template>
  <div id="app">
    <div id="nav">
      <a href="#"><MenuIcon /></a>
      <router-link to="/"><HomeIcon /></router-link>
      <router-link to="/page"><CardIcon /></router-link>
      <router-link to="/page"><DrawerIcon /></router-link>
      <router-link to="/page"><FolderIcon /></router-link>
    </div>
    <div id="content">
      <router-view/>
    </div>
  </div>
</template>
<script>
import MenuIcon from './assets/menu.svg'
import HomeIcon from './assets/home.svg'
import CardIcon from './assets/card.svg'
import DrawerIcon from './assets/drawer.svg'
import FolderIcon from './assets/folder.svg'

export default {
  name: 'App',
  components: {
    MenuIcon,
    HomeIcon,
    CardIcon,
    DrawerIcon,
    FolderIcon
  }
}
</script>
<style lang="scss">
html,
body {
  height: 100%;
}

body {
  margin: 0;
}

#app {
  height: 100%;
  font-family: 'Roboto', sans-serif;

  #nav {
    float: left;
    width: 50px;
    height: 100%;
    text-align: center;
    background-color: #4676f0;

    a {
      display: block;
      margin: 30px 0;
      line-height: 0;

      &.router-link-exact-active {
        svg {
          path {
            fill: #77bbff;
          }
        }
      }
    }
  }

  #content {
    position: absolute;
    left: 50px;
    top: 0;
    right: 0;
    bottom: 0;
    padding: 0 18px;
    background-color: #e5e5e5;
  }
}
</style>
