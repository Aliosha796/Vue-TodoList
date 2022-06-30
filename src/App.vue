<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";
export default {
  components: {
    TodoHeader,
    TodoList,
    TodoFooter,
  },
  data() {
    return {
      Todos: JSON.parse(localStorage.getItem("Todos")) || [
        { id: "001", title: "30分钟力量训练", done: false, isEdit: false },
        { id: "002", title: "看一篇英语文章", done: true, isEdit: false },
        {
          id: "003",
          title: "学20分钟口琴",
          done: false,
          isEdit: false,
        },
      ],
    };
  },
  methods: {
    //添加数据
    AddTodoItem(Item) {
      this.Todos.unshift(Item);
    },
    //标记完成
    CheckTodo(id) {
      //遍历Todos数组，并将done值取反
      this.Todos.forEach((todo) => {
        if (todo.id === id) {
          todo.done = !todo.done;
        }
      });
    },
    //删除单个列表事项
    DelTodo(id) {
      this.Todos = this.Todos.filter((todo) => {
        return todo.id !== id;
      });
    },
    //一键删除所有事项
    DeleteArray() {
      this.Todos.splice(0);
    },
  },
  watch: {
    //监视数据变化并存入浏览器
    Todos: {
      deep: true /* 深度监视开启 */,
      handler(value) {
        localStorage.setItem("Todos", JSON.stringify(value));
      },
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="containerMain">
      <TodoHeader :AddTodoItem="AddTodoItem"></TodoHeader>
      <TodoList
        :Todos="Todos"
        :CheckTodo="CheckTodo"
        :DelTodo="DelTodo"
      ></TodoList>
      <TodoFooter :Todos="Todos" :DeleteArray="DeleteArray"></TodoFooter>
    </div>
  </div>
  <img src="./assets/img/background.jpg" class="background" alt="" />
</template>

<style>
body {
  margin: 0;
  padding: 5vh;
  /* background: linear-gradient(
    to right,
    rgb(199, 210, 254),
    rgb(254, 202, 202),
    rgb(254, 249, 195)
  ); */
}
h1 {
  color: #fff;
}
.container {
  text-align: center;
  width: 80%;
  box-shadow: 0 2px 4px 0 rgb(0 0 0 / 20%), 0 2.5rem 5rem 0 rgb(0 0 0 / 10%);
  margin: auto;
  padding: 10px 0 10px 0;
  border-radius: 20px;
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
}
@media screen and (max-width: 400px) {
  body {
    padding: 0;
  }
  .container {
    width: 100%;
    margin: 0;
    border-radius: 0px;
  }
  .containerMain {
    width: 100%;
  }
}
.containerMain {
  margin: auto;
  width: 90%;
}
.background {
  width: 100%;
  height: 100%;
  position: fixed;
  object-fit: cover;
  top: 0;
  left: 0;
  z-index: -999;
}
</style>
