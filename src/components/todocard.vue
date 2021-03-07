<template>
  <div class="todocard">
    <div class="header">
      <p>{{today}}</p>
      <h2 class="has-text-primary">{{title}}</h2>
      <p>{{items.length}} tâches</p>
    </div>
    <div class="body">
      <div class="new">
        <newtodo @newTask = "addTask"/>
      </div>
      <div class="list">
        <todolist v-bind:tasks = "items" @check = "checkTask"  @remover = "removeTask"/>
      </div>
    </div>
  </div>
</template>

<script>
import newtodo from '@/components/newtodo.vue'
import todolist from '@/components/todolist.vue'
export default {
  name: "todocard",
  components: {
    newtodo,
    todolist
  },
  props: {
    title: null,
  },
  data: function() {
    return {items: []}
  },
  computed: {
    today: function() {
      return new Date().toLocaleString("fr-FR", { weekday:"long" ,day:"numeric", month:"long"});
    }
  },
  methods: {
    addTask(task) {
      this.items.push({description: task, done: false});
    },

    checkTask(index) {
      this.items[index].done = !this.items[index].done;
    },

    removeTask(index) {
      this.items.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todocard {
  background-color: white;
}

.header {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 3rem;
  font-weight: 700;
  box-shadow: 0 4px 6px grey;
}

.body .new{
  display: flex;
  justify-content: center;
}

.body .list{
  display: flex;
  justify-content: space-between;
}
</style>
