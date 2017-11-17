<template>
    <div id="toolbar">
      <i class="logo"><img src="../assets/logo.png" width="30" height="30"></i>
      <i @click="newNote" class="el-icon-plus"></i>
      <i @click="toggleFavorite" class="el-icon-upload" :class="{starred: activeNote.favorite}"></i>
      <i @click="deleteNote" class="el-icon-delete"></i>
    </div>
</template>
<style lang="scss" scoped>
 #toolbar{
    float: left;
    width: 60px;
    height: 100%;
    background-color: #30414D;
    color: #767676;
    padding: 35px 25px 25px 25px;
  }
i{
  display: inline-block;
  height: 100%;overflow: hidden;
  margin-bottom: 54px;
  cursor: pointer;
  opacity: 0.6;
  transition: opacity 0.5s ease;
   &:hover{
        opacity: 1;
      }
}
i:before{
  display: inline-block;
  font-size: 30px;
  color: #666a6d;
}
.starred:before {
    color: #F7AE4F;
  }
</style>

<script>
import { mapActions, mapState } from 'vuex';
export default {
  name: 'Toolbar',
  methods: mapActions([
    'newNote',
    'toggleFavorite',
    'deleteNote'
  ]),
  computed: mapState([
    'activeNote'
  ])
}
</script>
