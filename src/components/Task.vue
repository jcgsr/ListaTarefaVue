<template>
  <div @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
  export default {
    props: {
      task: { type: Object, required: true}
    },
    computed: {
      stateClass() {
        return {
          pending: this.task.pending,
          done: !this.task.pending
        }
      }
    }
  }
</script>

<style>
.task {
  position: relative;
  box-sizing: border-box;
  width: 20rem;
  height: 5rem;
  padding: 10px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

.pending {
  border-left: 12px solid #102236;
  background-color:  #112e50;
}

.done {
  color: #ddd;
  border-left: 12px solid rgb(5, 6, 24);
  background-color: rgb(10, 12, 53);
  text-decoration: line-through;
}

.pending .close {
  background-color: #102236;
}

.done .close {
  background-color: rgb(5, 6, 24);
}

.close {
  position: absolute;
  right: 10px;
  top: 10px;
  font-size: .9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
</style>
