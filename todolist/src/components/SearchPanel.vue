<template>
  <div>
    <input :value="modelValue" placeholder="Type to search" @input="onInput" />
  </div>
</template>

<script>
export default {
  emits: ["onSearch", "update:modelValue"],
  // props: ["value"],
  props: ["modelValue"],
  methods: {  
    onInput(e) {
      this.$emit("update:modelValue", e.target.value);
    },
  },
};
</script>
