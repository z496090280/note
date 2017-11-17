<template>
  <div type="border-card" id="notes-list">
    <h2>笔记列表<span></span>区草的笔记本</h2>
    <!-- all -->
    <el-button type="primary" icon="el-icon-search" @click="toggleShow('all')" :class="{active: show === 'all'}">全部笔记</el-button>
    <!-- favorite -->
    <el-button type="primary" @click="toggleShow('favorite')" :class="{active: show === 'favorite'}">云笔记<i class="el-icon-upload el-icon--right"></i></el-button>
    <!-- search -->
    <el-input
      placeholder="请输入笔记名查找"
      prefix-icon="el-icon-search"
      v-model="search"
      class="el-icon-search">
    </el-input>
    <!--测试搜索框-->

    <!-- 渲染笔记列表 -->
    <div class="list-item">
      <div class="item" v-for="(note,index) in searhNotes" :key="index" :class="{active: activeNote === note}" @click="updateActiveNote(note)">{{note.title.trim().substring(0,30)}}</div>
    </div>
  </div>
</template>
<style lang="scss" scoped>
  #notes-list{
    float: left;
    width:300px;
    height:418px;
    background: #f5f5f5;
    color:#30414D;
  }
  #notes-list h2{
    font-weight: normal;
    font-size: 20px;
    margin:0;
    padding:10px 0;
  }
  #notes-list h2 span{
    display: inline-block;
    background:#666;
    width: 1px;
    height:21px;
    margin:0 10px;
    vertical-align: text-bottom;
  }
  #notes-list button{
    margin-bottom: 20px;
    padding:10px 30px;
    background:#fff;
    border:1px solid #999;
  }
  #notes-list button.active{
    background:#e8e3e3;
  }
  .el-button--primary{
    color:#30414D;
  }
  .list-item .item{
    background:#666;
    color:#fff;
    border-bottom:1px solid #fff;
    height:39px;
    line-height: 39px;
    text-align: left;
    text-indent: 2em;
  }
  .list-item .item:hover{
    background:#337ab7;
  }
  .list-item .item.active{
    background:#337ab7;
  }
  .el-input{
    margin-bottom:20px;
  }
  .el-icon-search:before{
    position: absolute;
    color: #bfcbd9;
    top: 10px;
    right: 10px;
  }
  .el-input, .el-input__inner{
    width: 80%;
  }

</style>

<script>
import { mapGetters, mapState, mapActions } from 'vuex';
    export default{
      name:'NotesList',
      data(){
        return{
          search:""
        }
      },
      computed:{
        ...mapGetters([
            'filteredNotes'
          ]),
        //state 内部状态
        ...mapState([
            'show',
            'activeNote'
          ]),
        // 计算属性，自定义过滤
        searhNotes(){
          if(this.search.length>0){
            return this.filteredNotes.filter((note)=>note.title.toLowerCase().indexOf(this.search)>-1)
          }else{
            return this.filteredNotes
          }
        }
      },
      methods:{
        ...mapActions([
            'toggleListShow',
            'setActiveNote'
          ]),
        // 切换列表，全部或者收藏
        toggleShow(type){
          this.toggleListShow({show:type})
        },
         // 点击列表，更新当前激活文章
        updateActiveNote(note){
          this.setActiveNote({note})
        }
      }
    }
</script>
