<template>
  <fieldset @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </fieldset>
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
fieldset {
  display: flex;
  border: none; 
  padding: 0;
  margin: 0;
}

fieldset p {
  display: flex;
  justify-content: center; 
  align-items: center;  
  margin: auto; 
  color: beige;
}

.task {
  position: relative;
  box-sizing: border-box;
  width: 20rem;
  height: 5rem;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

.pending {
  border-left: 12px solid rgb(7, 7, 150);
  background-color:  #0a0455;
}

.done {
  color: #ddd;
  border-left: 12px solid rgb(15, 14, 14);
  background-color: rgb(12, 1, 1);
  text-decoration: line-through;
}

.pending .close {
  background-color: rgb(7, 7, 150);
  color: beige;
}

.done .close {
  background-color:  rgb(21, 21, 22);
}

.close {
  position: absolute;
  right: 2px;
  top: 2px;
  font-size: .9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
</style>
