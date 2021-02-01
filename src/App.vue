<template>
  <div id="app">
    <h1>Tasks</h1>
    <NewTask @taskAdded="addTask" />
    <Tasks :tasks="tasks" @taskDeleted="deleteTask" />
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
import NewTask from "./components/NewTask.vue";

export default {
  components: { Tasks, NewTask },
  data() {
    return {
      tasks: [],
    };
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
