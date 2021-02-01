<template>
  <div class="new-task">
    <input
      class="form-element"
      v-model="title"
      @keydown.enter="addTask"
      type="text"
      placeholder="Nova tarefa..."
    />

    <button class="form-element" @click="addTask">+</button>
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
.new-task {
  margin: 35px;
}

.form-element {
  outline: none;
  font-size: 2rem;
  border: 1px solid #fff;
  padding: 5px 10px 8px;
  color: #fff;
}

input.form-element {
  width: 500px;
  background-color: #fff2;
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
}

button.form-element {
  border-left: none;
  background-color: #2196f3;
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;
}
</style>
