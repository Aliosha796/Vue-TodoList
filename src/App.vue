<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
export default{
      components:{
        TodoHeader,TodoList,TodoFooter
      },
      data() {
        return {
          Todos:
          JSON.parse(localStorage.getItem('Todos')) ||
          [
            {id:'001',title:'下午三点去打网球',done:false},
            {id:'002',title:'晚上7点半去图书馆',done:true},
            {id:'003',title:'睡前规划',done:false},
          ]
        }
      },
      methods: {
        //添加数据
          AddTodoItem(Item){
            this.Todos.unshift(Item)
            
          },
          //标记完成
          CheckTodo(id){
            //遍历Todos数组，并将done值取反
            this.Todos.forEach((todo) => {
              if(todo.id === id){
                todo.done = !todo.done
              }
            })
          },
          //删除单个列表事项
          DelTodo(id){
              this.Todos = this.Todos.filter((todo) => {
                return todo.id !== id
              })

          },
          //一键删除所有事项
          DeleteArray(){
            this.Todos.splice(0)
            
          }

      },
      watch:{
        //监视数据变化并存入浏览器
        Todos:{
          deep:true,/* 深度监视开启 */
          handler(value){
            localStorage.setItem('Todos',JSON.stringify(value))
          }
        }
      },
      
      
}
</script>

<template>
  <div class="container">
    <div class="containerMain">
      <TodoHeader :AddTodoItem="AddTodoItem"></TodoHeader>
      <TodoList :Todos="Todos" :CheckTodo="CheckTodo" :DelTodo="DelTodo"></TodoList>
      <TodoFooter :DeleteArray="DeleteArray"></TodoFooter>
      </div>
  </div>
</template>

<style>
@font-face {
  font-family: 'iconfont';  /* Project id 3291689 */
  src: url('//at.alicdn.com/t/font_3291689_fefeq28qadd.woff2?t=1648999064622') format('woff2'),
       url('//at.alicdn.com/t/font_3291689_fefeq28qadd.woff?t=1648999064622') format('woff'),
       url('//at.alicdn.com/t/font_3291689_fefeq28qadd.ttf?t=1648999064622') format('truetype');
}
body{
    margin: 0;
    padding: 0;

}
.container{
    text-align: center;
    width:90%;
    box-shadow: 0 2px 4px 0 rgb(0 0 0 / 20%), 0 2.5rem 5rem 0 rgb(0 0 0 / 10%);
    margin: auto;
    margin-top: 2%;
    padding: 10px 0 10px 0;
    
}
@media screen and (max-width: 400px) {
  
    .container{
        width: 100%;
        margin: 0;
        
    }
    .containerMain{
        width: 100%;
    }
    
  }
.containerMain{
    margin: auto;
    width: 90%;
    
    
    

}
</style>
