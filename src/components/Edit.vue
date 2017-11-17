<template>
  <div id="edit">
    <!-- <el-input type="textarea" autosize placeholder="输入笔记标题" @input="updateNote" v-model="currentNote.title">
    </el-input>
    <div style="margin: 20px 0;"></div>
    <el-input type="textarea" placeholder="请输入笔记内容....." v-model="currentNote.content" @input="updateNote">
    </el-input> -->
    <!--测试textarea-->
    <el-input  placeholder="请输入内容" @input="updateNote" v-model="currentNote.title"></el-input>
    <textarea name="" id="" cols="30" rows="17" placeholder="请输入笔记内容....." v-model="currentNote.content" @input="updateNote"></textarea>
  </div>
</template>

<style lang="scss" scoped>
#edit{
  float: left;
  width: 500px;
  background: #f5f5f5;
  height: 420px;
}
textarea{
    display: block;
    resize: vertical;
    padding: 5px 15px;
    line-height: 1.5;
    box-sizing: border-box;
    width: 100%;
    font-size: 14px;
    color: #5a5e66;
    background-color: #fff;
    background-image: none;
    border: 1px solid #d8dce5;
    border-radius: 4px;
    transition: border-color .2s cubic-bezier(.645,.045,.355,1);
    margin-top: 14px
}
</style>

<script>
import { mapState, mapActions, mapGetters } from 'vuex'
    export default{
      name:'Edit',
      computed:{
        ...mapGetters([
            'activeNote'
          ]),
        currentNote(){
          return this.activeNote
        }
      },
      methods: {
        ...mapActions({
          update: 'updateNote'
        }),

        updateNote() {
          this.update({
            note: this.currentNote
          });
        }
      }
    }
</script>
