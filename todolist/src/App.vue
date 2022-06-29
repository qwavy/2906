<template>
  <div>
    <!-- <search-panel :value="searchValue" @onSearch="onSearch" /> -->

    <search-panel v-model="searchValue" />
    <task-counter />
    <todo-list :tasks="filteredTodos" :onToggleDone="onDone" @handleDelete="onDelete" />
    <p>done {{doneFunc}}, import {{importantFunc}}, all {{Counterfunc}}</p>
    <filter-buttons :value="selectedCategory" @change="filteredFunc" />
    {{selectedCategory}}
    <form-add-task @onAdd="onAdd" />
  </div>
</template>

<script>
import SearchPanel from "./components/SearchPanel.vue";
import TodoList from "./components/TodoList.vue";
import FormAddTask from "./components/FormAddTask.vue";
import FilterButtons from "./components/FilterButtons.vue";
import TaskCounter from "./components/TaskCounter.vue";
export default {
  components: {
    SearchPanel,
    TaskCounter,
    TodoList,
    FormAddTask,
    FilterButtons
    // HTitle: HeaderTitle,
  },
  data() {
    return {
      selectedCategory: "all",
      title: "Welcome to my TodoList",
      todos: [
        { id: 1, text: "Learn VueJS", important: true, done: false },
        { id: 2, text: "Drink Coffee", important: false, done: false },
        { id: 3, text: "Drink Water", important: false, done: true }
      ],
      // done_counter: this.filteredTodos,
      all_counter: this.todos,
      searchValue: ""
    };
  },
  computed: {
    foundTasks() {
      return this.todos.filter(todo =>
        todo.text.toLowerCase().includes(this.searchValue.toLowerCase())
      );
    },
    filteredTodos() {
      //   ? this.todos.filter((item) => item.important === this.selectedArticle)
      //   : this.todos;
      // return data;

      // const data = this.selectedCategory
      // if (data == null) {
      //   return this.todos
      // } else{
      //   const result = this.todos.filter((todos) => todos.important === data)
      //   // this.filtered = result
      //   // return this.filtered
      //   return result
      // }
      if (this.selectedCategory === "important") {
        return this.todos.filter(todo => todo.important);
      } else if (this.selectedCategory === "done") {
        return this.todos.filter(todo => todo.done);
      } else {
        return this.todos;
      }
    },
    Counterfunc() {
      const count = this.todos.filter(function(value) {
        return value;
      });
      return count.length;
    },
    importantFunc() {
      // const count = this.todos.filter(function(value) {
      //   return value;
      // });
      const count = this.todos.filter(todo => todo.important)
      return count.length;
    },
    doneFunc(){
      const count = this.todos.filter(todo => todo.done)
      return count.length;
    }
  },
  methods: {
    filteredFunc(category) {
      this.selectedCategory = category;
    },
    showAll() {
      this.selectedCategory = "all";
    },
    onSearch(value) {
      this.searchValue = value;
    },
    onDone(id) {
      if (!id) {
        throw "Id is not provided";
      }

      const idx = this.todos.findIndex(item => item.id === id);
      this.todos[idx].done = !this.todos[idx].done;
    },
    onImportant(id) {
      if (!id) {
        throw "Id is not provided";
      }

      const idx = this.todos.findIndex(item => item.id === id);
      this.todos[idx].important = !this.todos[idx].important;
    },
    onDelete(id) {
      const idx = this.todos.findIndex(item => item.id === id);
      this.todos.splice(idx, 1);
    },
    onAdd(text = "Task") {
      const obj = {
        id: this.todos.length + 1,
        text,
        done: false,
        important: false
      };
      this.todos.push(obj);
    }
  }
};
</script>

<style>
</style>
