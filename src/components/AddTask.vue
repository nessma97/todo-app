<template>
<div class="container mx-auto">
      <form @submit.prevent="addTodo" class="todo__from" >
        <div class="add__todo">
          <input type="text" placeholder="Way to go tiger... " class="rounded-lg p-1.5" v-model="task">
          <button>Add task</button>
        </div>
        <button @click="removeAll" class="remove__all">Remove All todos</button>
      </form>
  </div>
</template>

<script>
export default {
  name: 'AddTask',
  data () {
    return {
      task: ''
    }
  },
  methods: {
    addTodo () {
      if (this.task.length === 0) return
      // if (!this.task) return
      this.$emit('toDo__added', { task: this.task })
      this.task = ''
    },
    removeAll () {
      this.$emit('allRemoved')
    }
  }
}
</script>

<style scoped>
@import '../assets/styles/main.css';

.add__todo input[type="text"] {
  border:1px solid var(--light-moov);
  border-right: none;
  border-radius: 5px 0px 0px 5px;
  transition: border .3s ease-in-out;
  padding: 5px;
  width: 100%;
  max-width: 40%;
  margin: 10px 5px 10px 15px;
}

.add__todo input[type="text"]:hover {
  border-color: var(--dark-moov);
}

.add__todo button {
  background-color: var(--light-moov);
  padding: 5px;
  color: white;
  border:none;
  border-radius: 0px 5px 5px 0px;
  margin-left:-6px;
  padding: 6px;
  cursor: pointer;
  text-align: center;
  transition: border .3s ease-in-out;
}

.add__todo button:hover {
  background-color: var(--secondary-color);
}

.remove__all {
width: 75%;
padding: 5px;
background-color: var(--light-moov);
border-radius: 10px;
margin-left: 13px;
color: white;
transition: border .5s ease-in-out;
}

.remove__all:hover {
  background-color: var(--secondary-color);
}
</style>
