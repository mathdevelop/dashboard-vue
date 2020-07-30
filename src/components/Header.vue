<template>
  <div id="header">
    <div id="search">
      <SearchIcon />
      <input type="text" placeholder="O que você procura?">
    </div>
    <div id="actions">
      <a href="#"><EditIcon /></a>
      <a href="#"><AlertIcon /></a>
      <a href="#"><ProfileIcon /></a>
    </div>
  </div>
</template>

<script>
import SearchIcon from '@/assets/search.svg'
import EditIcon from '@/assets/edit.svg'
import AlertIcon from '@/assets/alert.svg'
import ProfileIcon from '@/assets/profile.svg'

export default {
  name: 'Header',
  components: {
    SearchIcon,
    EditIcon,
    AlertIcon,
    ProfileIcon
  }
}
</script>

<style scoped lang="scss">
#header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 50px;

  #search {
    display: flex;

    input {
      margin-left: 15px;
      padding: 0;
      border: 0;
      background: 0;
      outline: 0;
      font-family: 'Rubik', sans-serif;
      font-size: 16px;
      color: #b4b4b4;
    }
  }

  #actions {
    a {
      margin: 0 15px;
    }
  }
}
</style>
