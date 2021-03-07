<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <todocard/>
    <newtodo/>
  </div>
</template>

<script>
// @ is an alias to /src
import todocard from '@/components/todocard.vue'
import newtodo from '../components/newtodo.vue'

export default {
  name: 'Home',
  components: {
    todocard,
    newtodo
  }
}
</script>
