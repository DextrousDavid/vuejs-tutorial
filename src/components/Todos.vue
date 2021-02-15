<template>
  <div>
      <h3>Todos</h3>
      <div class="todos">
      <div class="todo" v-for="todo in allTodos" :key="todo.id">
          {{ todo.title }} <i @click="deleteTodo(todo.id)" class="fa fa-trash-alt"></i>

      </div>
      </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
computed: {
    ...mapGetters([
        'allTodos'
    ])
},

methods: {
 ...mapActions(['fetchTodos', 'deleteTodo']),
},

mounted() {
    this.fetchTodos()
},
}
</script>

<style scoped>
.todos {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
}

.todo {
    border: 1px solid rgb(122, 82, 82);
    background: #1f9eda;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;
    color: #fff
}

i {
    position: absolute;
    bottom: 10px;
    right: 10px;
    color: #fff;
    cursor: pointer;
}
</style>