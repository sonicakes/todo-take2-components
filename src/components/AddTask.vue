<template>
  <div>
    <input type="text" placeholder="add task here..." v-model="addedTask" />
    <button @click="addTask">Add</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      addedTask: "",
    };
  },
  emits: ["new-added"],
  methods: {
    addTask() {
      this.$emit("new-added", this.addedTask);
    },
  },
};
</script>
