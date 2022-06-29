<template>
  <li class="todo_item" :class="{ important_task: important, done }">
    {{ text }}
    <button @click="onDone()">Important</button>
    <button @click="onDone()">Done</button>
    <button @click="onDelete">Delete</button>
  </li>
</template>

<script>
export default {
  emits: ["deleteItem"],

  props: {
    text: { type: String, required: true },
    done: { type: Boolean, default: false },
    important: { type: Boolean, default: false },
    onDone: Function,
  },
  methods: {
    onDelete() {
      this.$emit("deleteItem");
    },
  },
};
</script>

<style scoped>
.todo_item {
  font-family: "Century Gothic";
  list-style: none;
  padding: 8px 12px;
  display: block;
  border: 1px solid #ccc;
  border-radius: 8px;
  margin-bottom: 12px;
}

.important_task {
  font-weight: bold;
  color: slateblue;
}

.done {
  text-decoration: line-through;
}
</style>
