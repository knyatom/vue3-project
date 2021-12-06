<template>
  <div class="container">
    <h1> To-do List</h1>
    <form class="d-flex">
      <div class="flex-grow-1 mr-2">
       <input type="text" class="form-control" v-model="todo" placeholder="Type Text">
      </div> 
      <button class="btn btn-primary" @click="onSubmit">
        Add
      </button>
    </form>
    {{todos}}
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  setup(){
   const todo=ref('');
   const todos=ref([]);
   const onSubmit=(e)=>{
     e.preventDefault();
     console.log(todo.value);
     todos.value.push({
       id:Date.now(),
       subject:todo.value
     })
   }   
    return {
      todo,todos,onSubmit
     }
  }
};
</script>

<style>

</style>
