<template>
  <ul>
    <new-title title="title" />
    <todo-list-item v-for="item in tasks" :key="item.id" :text="item.text" :done="item.done" :important="item.important"
      :onDone="() => onToggleDone(item.id)" @deleteItem="$emit('handleDelete', item.id)" />
    <!-- <h2>filtered</h2> -->
    <!-- <todo-list-item v-for="item in filtered" :key="item.id" :text="item.text" /> -->
  </ul>
  <button @click="showImportant">import</button>
</template>

<script>
import TodoListItem from "./TodoListItem.vue";
export default {
  emits: ["handleDelete"],
  props: {
    tasks: Array,
    filtered: Array,
    onToggleDone: Function,
  },
  components: { TodoListItem },
  methods: {
    showImportant(id) {
      // const idx = this.tasks.findIndex((item) => item.id === id);
      // console.log(idx)
      // const idx = this.tasks.length
      console.log(id)
      // if(this.tasks[1].important){
      //   alert('true')
      // }
      // const r = this.tasks.filter((todos) => todos.important === this.tasks.important)
      const r = this.tasks.map((tasks ) => tasks)
      console.log(r)
      
    }
  }
};
</script>

