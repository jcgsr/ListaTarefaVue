<template>
   <div class="tasks-progress animate__animated animate__shakeX">
      <span class="progress-value">{{ progress }}%</span>
      <div class="progress-bar" :style="{width: progress + '%'}"></div>
   </div>
</template>

<script>
export default {
   props: {
      progress: {type: Number, default: 0}
   }
}
</script>

<style>
   .tasks-progress {
      position: relative;
      width: 80%;
      border: 1px solid #0a0455;
      color:#0a0455;
      border-radius: 8px;
      margin-bottom: 15px;
      display: flex;
      flex-direction: column;
      align-items: center;
   }

   .progress-bar {
      position: absolute;
      border-radius: 8px;
      height: 100%;
      background-color: rgb(106, 106, 128);
      align-self: flex-start;
      color: #0a0455;
   }

   .progress-value {
      z-index: 1;
      font-size: 1.5rem;
   }
</style>