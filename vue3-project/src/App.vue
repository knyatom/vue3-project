<template>
  <div class="container">
    <hr />
    <h1>To-do List</h1>
    <form @submit.prevent="onSubmit">
      <div class="d-flex mr-2">
        <input
          type="text"
          class="form-control"
          v-model="todo"
          placeholder="Type Text"
        />
        <button class="btn btn-primary ml-2" type="submit">Add</button>
      </div>
      <div v-if="hasError" style="color: red">This field cannot be empty</div>
    </form>

    <div class="card mt-2" v-for="todo in todos" v-bind:key="todo.id">
      <div class="card-body p-2">
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            v-model="todo.completed"
          />
          <label class="form-check-label"
          :class="{todo:todo.completed} "
          > {{ todo.subject }} </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const hasError = ref(false);
    const todo = ref("");
    const todos = ref([]);
    const todoStyle={ 
          textDecoration:'line-through',
          color:'gray'
    }    

    const onSubmit = () => {
      if (todo.value === "") {
        hasError.value = true;
      } else {
        todos.value.push({
          id: Date.now(),
          subject: todo.value,
          completed: false,
        });
        hasError.value = false;
        todo.value = "";
      }
    };

    return {
      todo,
      todos,
      onSubmit,
      hasError,
      todoStyle
    };
  },
};
</script>

<style>
.name {
  color: red;
}
.todo{
  color:gray;
  text-decoration:line-through;
}
</style>
