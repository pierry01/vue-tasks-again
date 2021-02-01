<template>
  <div class="new-task">
    <input v-model="title" @keydown.enter="addTask" type="text" />
    <button @click="addTask">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTask() {
      this.$emit("taskAdded", { title: this.title });
      this.title = "";
    },
  },
};
</script>

<style>
</style>
