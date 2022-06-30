<template>
  <li>
    <section class="listTitle" @click="Checkdone(Todos.id)">
      <p v-show="!Todos.isEdit" :class="{ checked: Todos.done }">
        {{ Todos.title }}
      </p>
      <input
        type="text"
        class="editInput"
        v-show="Todos.isEdit"
        v-model="NewEdit"
        @blur="handleBlur(Todos)"
        ref="inputTitle"
      />
    </section>

    <!-- 事项名称 -->
    <div class="operation">
      <!-- 编辑按钮 -->
      <span v-show="!Todos.isEdit" class="edit" @click="EditItem(Todos)"
        >&#xe602;</span
      >
      <span @click="DelItem(Todos.id)" :title="delTitle" class="del"
        >&#xe600;</span
      ><!-- 删除按钮 -->
    </div>
  </li>
</template>
<script>
export default {
  props: ["Todos", "CheckTodo", "DelTodo"],
  data() {
    return {
      delTitle: "删除此事项",
      editTitle: "修改",
      NewEdit: this.Todos.title,
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
    EditItem(Todos) {
      Todos.isEdit = true;
      this.$nextTick(() => {
        this.$refs.inputTitle.focus();
      });
    },
    handleBlur(Todos) {
      Todos.isEdit = false;
      if (this.NewEdit == "") {
        return alert("输入不能为空");
      } else {
        Todos.title = this.NewEdit;
      }
    },
  },
};
</script>
<style scoped>
#doingThings li {
  position: relative;
  font-size: 1.2em;
  box-sizing: content-box;
  min-height: 60px;
  cursor: pointer;
  list-style: none;
  display: flex;
  align-items: stretch;
  background-color: rgba(255, 255, 255, 0.6);
  margin-top: 5px;
  backdrop-filter: blur(30px);
  letter-spacing: 2px;
  border: 0;
  border-radius: 10px;
}

#doingThings li:hover {
  background-color: rgb(167, 165, 165);
}

.checked {
  text-decoration: line-through 5px;
}

.editInput {
  border-top: 0;
  border-left: 0;
  border-right: 0;
  border-bottom: 1px #000 solid;
  outline: 0;
  height: 100%;
  background-color: rgba(255, 255, 255, 0);
  font-size: 1.2em;
  margin-left: 20px;
}

.listTitle {
  width: 90%;
  display: flex;
  align-items: center;
}
.listTitle p {
  margin-left: 20px;
}
.operation {
  font-family: "iconfont";
  width: 120px;
  display: none;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.operation span {
  width: 50%;
  display: flex;
  height: 100%;
  justify-content: center;
  align-items: center;
  font-size: 1.5rem;
}
.operation .del:hover {
  background-color: red;
  color: #fff;
}
.operation .edit:hover {
  background-color: rgb(88, 61, 237);
  color: #fff;
}
</style>
