<template>
  <div class="newtodo">
    <form>
      <input placeholder="Nouvelle tâche..." v-model="task"/>
      <div>
        <button class="button is-primary"  v-on:click="sendTask"><i class="fas fa-plus"></i></button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "newtodo",
  data() {
    return {task: "",}
  },
  methods:{
    sendTask: function() {
      if (this.task != ""){
        this.$emit("newTask", this.task);
        this.task = "";
      }
    }
  },
  computed: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  display: flex;
  justify-content: center;
  align-items: center;
}

input {
  border: none;
  border-bottom: 1px solid #00c4a7;
  padding: 0.5rem;
  margin: 2rem 0;
  width: 20rem;
  outline: none;
}

.newtodo div {
  width: 3rem;
  height: 3rem;
}

.newtodo div button {
  display: block;
  width: 100%;
  height: 100%;
  border-radius: 50%;
}
</style>
