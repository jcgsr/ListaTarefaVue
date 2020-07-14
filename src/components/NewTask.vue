<template>
  <div class="new-task animate__animated animate__flash">
    <input
      v-model="name"
      @keydown.enter="add"
      type="text"
      class="form-element"
      placeholder="Nova Tarefa"
    />
    <button @click="add" class="form-element">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: ""
    };
  },
  methods: {
    add() {
      this.$emit("taskAdded", { name: this.name });
      this.name = "";
    }
  }
};
</script>

<style>
.new-task {
   margin: 35px;
}

.form-element {
   outline: none;
   font-size: 2rem;
   border: 1px solid #0a0455;
   padding: 5px 10px 8px;
   color: #0a0455;
}

input.form-element {
   width: 70%;
   background: #fff2;
   border-top-left-radius: 8px;
   border-bottom-left-radius: 8px;
}

button.form-element {
   border-left: none;
   background-color: #0a0455;
   border-top-right-radius: 8px;
   border-bottom-right-radius: 8px;
   color: beige;
}
</style>