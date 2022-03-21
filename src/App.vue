<template>
  <div class="container">
    <h6 class="text-center text-danger">
      Welcome to the Vuejs App 3 testing area
    </h6>
    <form @submit.prevent>
      <div class="form-group">
        <label for="formGroupExampleInput">My Todos</label>
        <input
          type="text"
          v-model="todo"
          class="form-control"
          id="formGroupExampleInput"
          placeholder="my todos"
        />
      </div>
    </form>
    <button class="btn btn-primary" @click="addTodo">Add</button>
    <div>
      <br /><br />

      <TodoList :lists="lists" @deleteItem="deleteTodo" />
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoList,
  },

  setup() {
    let todo = ref("");
    let lists = ref([]);

    function addTodo() {
      if (todo.value) {
        lists.value.push(todo.value);
        todo.value = "";
      }
    }
    function deleteTodo(index) {
      lists.value.splice(index, 1);
    }

    return {
      todo,
      lists,
      addTodo,
      deleteTodo,
    };
  },
};
</script>
