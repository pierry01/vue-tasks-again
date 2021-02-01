<template>
  <div class="tasks">
    <div>
      <div v-for="task in tasks" :key="task.title">
        {{ task.title }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
</style>
