<template>
  <div id="app">
    <ul>
      <Task
        v-for="task in tasks"
        :key="task.name"
        :name="task.name"
        :completed="task.completed"
        @complete="taskComplete"
      />
    </ul>
    <AddTask @new-added="addNewTask" />
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";
import Task from "./components/Task";

export default {
  name: "App",
  components: {
    Task,
    AddTask,
  },
  data() {
    return {
      tasks: [
        {
          name: "wash hair",
          completed: false,
        },
        {
          name: "walk the dogs",
          completed: true,
        },
      ],
    };
  },
  methods: {
    taskComplete(taskStatus) {
      this.tasks.forEach(function(arrayItem) {
        arrayItem.completed = taskStatus;
      });
    },
    addNewTask(task) {
      this.tasks.push({
        name: task,
        completed: false,
      });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.completed {
  color: red;
  text-decoration: line-through;
}
</style>
