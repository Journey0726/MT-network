<template>
  <div class="page-index">
   <el-row>
     <el-col :span="5"> <my-menu/></el-col>
     <el-col :span="19">
      1
     </el-col>
     <el-col :span="24">1</el-col>
   </el-row>
   <el-row></el-row>
  </div>
</template>

<script>
import myMenu from '@/components/index/menu.vue'
export default {
  components:{
    myMenu
  }
}
</script>

<style lang='scss'>
  @import '@/assets/css/index/index.scss';
</style>
