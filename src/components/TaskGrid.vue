<template id="grid">
  <div class="task-grid">
    <transition-group name="popup">
      <Task
        v-for="(task, i) in tasks"
        :key="task.name"
        @taskStateChanged="$emit('taskStateChanged', i)"
        @taskDeleted="$emit('taskDeleted', i)"
        :task="task"
      ></Task>
    </transition-group>

    <p v-if="tasks.length < 1" class="no-task">Sua vida está em dia 😃</p>
  </div>
</template>

<script>
import Task from "./Task.vue";
export default {
  components: { Task },
  props: {
    tasks: { type: Array, required: true }
  }
};
</script>

<style>
p {
  color: #0a0455;
}
.task-grid span {
  display: flex;
  justify-content: center;
}

.task-grid .task {
  margin: 10px;
}

.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
.popup-move {
  transition: all 300ms;
}
.popup-enter,
.popup-leave-to {
  transform: scale(0);
}
.popup-enter-active {
  transition: 400ms;
}
.popup-leave-active {
  transition: 400ms;
  position: absolute;
}
</style>
