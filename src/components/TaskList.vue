<template>
  <div id="task-list">
    <ul class="todos" v-for='(todo, i) in todos' :key="i">
      <li class="todos__items" >
        <span>{{ todo.task }}</span>
        <button @click="deleteTodo(i)" class="delete__btn">
          <img src="../assets/images/delete.png" alt="delete icon" class="delete-icon">
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TaskList',
  props: {
    todos: Array
  },
  methods: {
    deleteTodo (i) {
      this.$emit('deleted', { i })
    }
  }
}
</script>

<style>
.todos {
  width: 100%;
  max-width: 80%;
  margin-block: 10px;
  text-align: center;
}

.delete__btn {
    cursor: pointer;
    transition: border .5s ease-in-out;
    width: 7%;
}

.todos__items {
  display: flex;
  justify-content:space-between;
  align-items: center;
  margin: 10px 5px 15px 15px;
  color:var(--dark-moov);
  transition: border .3s ease-in-out;
  border-bottom: 2px solid var(--light-moov);
  padding: .5rem;
  }

  .todos__items:hover {
  border-color: var(--secondary-color);
  }

</style>
