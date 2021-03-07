<template>
  <div class="todolist">
    <div class="taches" v-for="(item, index) in tasks" :key="index">
      <div class="tache" >
        <input type="checkbox" name="task" v-on:click="check(index)" />
        <label for="task">{{ item.description }}</label>
      </div>
      <div class="button" v-on:click="remover(index)">
        <button><i class="fas fa-trash"></i></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "todolist",
  props: {
    tasks: {},
  },
  methods: {
      check(index) {
          this.$emit("check", index);
      },

      remover(index) {
          this.$emit("remover", index);
      }
  },
  computed: {},
};
</script>

<style scoped>
.todolist {
    display: block;
    margin: 1rem auto;
    width: 70%;
}

.todolist .taches{
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    margin-bottom: 0.5rem;
}

.todolist .tache input {
  margin-right: 2rem;
  width: 1rem;
  height: 1rem;
}

.todolist .tache.done{
    text-transform: line-through;
}

.todolist .button {
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  border: none;
  background-color: red;
}

.todolist .button button {
  display: block;
  height: 100%;
  border-radius: 50%;
  color: white;
  background-color: transparent;
  border: none;
  outline: none;
}
</style>