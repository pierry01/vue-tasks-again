<template>
  <div class="task" :class="stateClass">
    <p>{{ task.title }}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true,
    },
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending,
      }
    }
  }
};
</script>

<style>
.task {
  box-sizing: border-box;
  width: 250px;
  height: 125px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pending {
  border-left: 12px solid #B73229;
  background-color: #F44336;
}

.done {
  color: #DDD;
  border-left: 12px solid #0A8F08;
  background-color: #4CAF50;
  text-decoration: line-through;
}
</style>
