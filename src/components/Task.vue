<template>
  <transition    
    enter-active-class="animate_animated animate__zoomIn"
    leave-active-class="animate_animated animate__zoomOut"
  >
    <fieldset
      @click="$emit('taskStateChanged', task)"
      class="task animate__animated animate__zoomIn"
      :class="stateClass"
    >
      <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
      <p>{{ task.name }}</p>
    </fieldset>
  </transition>
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
