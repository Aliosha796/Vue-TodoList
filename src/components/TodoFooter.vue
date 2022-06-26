<template>
  <p>已完成{{ doneTotal }} / 全部 {{ Todos.length }}</p>
  <span @click="CleanAll" :title="title">&#xe628;</span>
</template>
<script>
export default {
  props: ["DeleteArray", "Todos"],
  data() {
    return {
      title: "删除全部事项",
    };
  },
  created() {},
  computed: {
    doneTotal() {
      let i = 0;
      this.Todos.forEach((todo) => {
        if (todo.done) i++;
      });
      return i;
    },
  },
  methods: {
    //删除全部事项的方法
    CleanAll() {
      if (confirm("确认全部删除？")) {
        this.DeleteArray();
      } else {
      }
    },
  },
};
</script>
<style scoped>
span {
  font-size: 1.5rem;
  font-family: "iconfont";
  cursor: pointer;
}

span:hover {
  color: red;
}
</style>
