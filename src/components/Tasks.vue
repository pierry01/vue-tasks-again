<template>
  <div class="tasks">
    <template v-if="tasks.length">
      <Task
        v-for="(task, id) in tasks"
        :key="task.title"
        :task="task"
        @taskDeleted="$emit('taskDeleted', id)"
        @taskStateChanged="$emit('taskStateChanged', id)"
      />
    </template>

    <p v-else class="no-task">Sua vida está em dia :)</p>
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  components: { Task },
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
.tasks {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.tasks .task {
  margin: 10px;
}

.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
</style>
