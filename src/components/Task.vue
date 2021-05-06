<template>
  <li @click="completeTask()">
    <h3 :class="isComplete ? 'completed' : ''">{{ name }}</h3>
  </li>
</template>

<script>
export default {
  props: ["name", "completed"],
  data() {
    return {
      isComplete: this.completed,
    };
  },
  emits: ["complete"],
  methods: {
    completeTask() {
      this.isComplete = !this.isComplete;
      this.$emit("complete", this.isComplete);
    },
  },
};
</script>
