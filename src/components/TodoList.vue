<template>
   <ul id="doingThings">
      <ListItem  
         v-for="TodosObj in Todos" 
         :key="TodosObj.id" 
         :Todos="TodosObj" 
         :CheckTodo="CheckTodo"
         :DelTodo="DelTodo"
         
         />
         
     
   </ul>
</template>
<script>
import ListItem from './ListItem.vue'
export default {
   props:['Todos','CheckTodo','DelTodo'],
   components:{
      ListItem
   },
   data() {
      return {
      }
   },
   created(){
   },
   computed:{
   },
   methods:{
   },
}
</script>
<style>
#doingThings{
    margin-top: 10px;
    padding: 0;
    width: 100%;
    display: flex;
    flex-direction: column;
}
</style>
