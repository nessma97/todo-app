<template>
  <div id="app" class="shadow-xl  bg-teal-400">
    <h1 class=" p-1">Add ToDos below</h1>
    <add-task @toDo__added="addTodo($event)" @allRemoved="removeAll($event)"/>
    <task-list :todos="todos" @deleted="deleteTodo($event)" />
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue'
import TaskList from './components/TaskList.vue'

export default {
  name: 'App',
  components: {
    AddTask,
    TaskList
  },
  data () {
    return {
      todos: []
    }
  },
  methods: {
    addTodo ({ task }) {
      this.todos.push({ task })
      // console.log(task)
      localStorage.setItem('todos', JSON.stringify(this.todos))
    },
    deleteTodo ({ i }) {
      this.todos.splice(i, 1)
      localStorage.getItem('todos', JSON.parse(this.todos))
    },
    removeAll () {
      this.todos = []
      // this.todos.length = 0
    }
  }
}
</script>

<style scoped>
#app {
  width: 40%;
  max-height: 50%;
  padding: 10px;
  margin: 100px auto;
  background-color: var(--main-color);
  border-radius: 10px;
}

#app h1 {
  font-style: italic;
  font-size: larger;
  font-weight: 400;
  margin-left: 15px;
  color: white;
}
</style>
