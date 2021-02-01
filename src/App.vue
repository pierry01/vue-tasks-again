<template>
  <div id="app">
    <h1>Tasks</h1>
    <TasksProgress :progress="progress" />
    <NewTask @taskAdded="addTask" />
    <Tasks
      :tasks="tasks"
      @taskDeleted="deleteTask"
      @taskStateChanged="toggleTaskState"
    />
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
import NewTask from "./components/NewTask.vue";
import TasksProgress from "./components/TasksProgress.vue";

export default {
  components: { Tasks, NewTask, TasksProgress },
  data() {
    return {
      tasks: [],
    };
  },
  computed: {
    progress() {
      const total = this.tasks.length;
      const done = this.tasks.filter((t) => !t.pending).length;

      return Math.round((done / total) * 100) || 0;
    },
  },
  methods: {
    addTask(task) {
      const sameTitle = (t) => t.title == task.title;
      const reallyNew = this.tasks.filter(sameTitle).length == 0;

      if (reallyNew) {
        this.tasks.push({
          title: task.title,
          pending: task.pending || true,
        });
      }
    },
    deleteTask(id) {
      this.tasks.splice(id, 1);
    },
    toggleTaskState(id) {
      this.tasks[id].pending = !this.tasks[id].pending;
    },
  },
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
