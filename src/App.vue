<template>
  <div id="app">
    <toggle-bar></toggle-bar>
    <notes-list></notes-list>
    <edit></edit>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  height: 100%;
  overflow: hidden;
}
</style>

<script>
import Edit from "./components/Edit";
import NotesList from "./components/NotesList";
import ToggleBar from "./components/ToggleBar";

export default {
  name: 'app',
  components:{
    Edit,
    NotesList,
    ToggleBar
  }
}
</script>


