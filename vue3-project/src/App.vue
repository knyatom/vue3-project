<template>
  <div class="container">
    <div v-if="toggle">true</div>
    <div v-else>false</div>
    <button @click="onToggle">toggle</button>
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
        <button class="btn btn-primary" type="submit">Add</button>
      </div>
      <div v-if="hasError" style="color: red">This field cannot be empty</div>
    </form>
    {{ todos }}
    <div class="card mt-2" v-for="todo in todos" v-bind:key="todo.id">
      <div class="card-body p-2">
        {{ todo.subject }}
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  setup() {
    const toggle = ref(false);
    const hasError = ref(false);
    const todo = ref("");
    const todos = ref([
      { id: 1, subject: "휴대폰사기" },
      { id: 2, subject: "장보기" },
    ]);
    const onSubmit = () => {
      //   e.preventDefault();
      console.log(todo.value);
      if (todo.value === "") {
        hasError.value = true;
      } else {
        todos.value.push({
          id: Date.now(),
          subject: todo.value,
        });
      }
    };
    const onToggle = () => {
      toggle.value = !toggle.value;
    };
    return {
      onToggle,
      todo,
      todos,
      onSubmit,
      toggle,
      hasError,
    };
  },
};
</script>

<style>
.name {
  color: red;
}
</style>
