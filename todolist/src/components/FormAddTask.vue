<template>
  <div>
    <!-- <input type="text" @input="onChange" :value="value" /> -->
    
    <input type="text" v-model="value" />
    <button @click="onClick">Add</button>
    {{ value }}
  </div>
</template>

<script>
export default {
  emits: ["onAdd"],
  data() {
    return {
      value: "",
    };
  },
  methods: {
    onChange(e) {
      this.value = e.target.value;
    },
    onClick() {
      this.$emit("onAdd", this.value);
      this.value = "";
    },
  },
};
</script>
