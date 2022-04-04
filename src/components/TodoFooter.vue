<template>
    <span @click="CleanAll" :title="title">&#xe628;</span>
</template>
<script>
export default {
   props:['DeleteArray'],
   data() {
      return {
         title:'删除全部事项'
      }
   },
   created(){
   },
   computed:{
   },
   methods:{
      CleanAll(){
         if(confirm("确认全部删除？")){
            this.DeleteArray()
         }
      }
   },
}
</script>
<style scoped>
span{
   font-size: 1.5rem;
   font-family: 'iconfont';
   cursor: pointer;
}
span:hover{
   color: red;
}
</style>
