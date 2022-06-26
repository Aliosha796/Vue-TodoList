<template>
  <li :class="{ checked: Todos.done }" @click="Checkdone(Todos.id)">
    <p>{{ Todos.title }}</p>
    <!-- 事项名称 -->
    <span @click="DelItem(Todos.id)" :title="title">&#xe66e;</span
    ><!-- 删除按钮 -->
  </li>
</template>
<script>
export default {
  props: ["Todos", "CheckTodo", "DelTodo"],
  data() {
    return {
      title: "删除此事项",
    };
  },
  created() {},
  computed: {},
  methods: {
    //点击完成事件的方法
    Checkdone(id) {
      this.CheckTodo(id);
    },
    //删除单个事项的方法
    DelItem(id) {
      if (confirm("是否删除？")) {
        this.DelTodo(id);
      }
    },
  },
};
</script>
<style scoped>
#doingThings li {
  padding: 0.2%;
  position: relative;
  font-size: 1.2em;
  box-sizing: content-box;
  min-height: 60px;
  cursor: pointer;
  list-style: none;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(233, 233, 233);
  letter-spacing: 2px;
  border-bottom: #000 2px dashed;
}

#doingThings li:hover {
  background-color: rgb(167, 165, 165);
}

.checked {
  text-decoration: line-through 5px;
}

span {
  top: 0;
  right: 0;
  position: absolute;
  font-family: "iconfont";
  height: 100%;
  width: 8vh;
  display: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

span:hover {
  color: white;
  background-color: red;
}
</style>
