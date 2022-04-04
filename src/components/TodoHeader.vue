<template>
      <h1>待办清单</h1>
      <p style="font-size: 1em;">有什么需要做的？</p>
      <input type="text" id="ListInput" placeholder="请输入内容并回车添加"  @keyup.enter="addNewItem"
     
      />
</template>
<script>
import { nanoid } from 'nanoid'
export default {
   props:['AddTodoItem'],
   data() {
      return {
      }
   },
   created(){
   },
   computed:{
   },
   methods:{
      addNewItem(InputList){
         const todoObj = {id:nanoid(),title:InputList.target.value,done:false}
         if(InputList.target.value === ''){
            alert("内容不能为空")
         }else{
            this.AddTodoItem(todoObj)
            InputList.target.value = ''
         }
        
      }
   },
}
</script>
<style>
#ListInput{
   width: 100%;
   height: 40px;
   border: #ccc 1px solid;
   font-size: 1.5em;
   box-sizing:border-box;
    
}

#ListInput::placeholder{
    font-size:0.7em;
}
</style>
