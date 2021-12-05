<template>
  <div :class="nameClass">
    <input type="text" v-model="name" />
    <button class="btn btn-primary" @click="onSubmit">Click</button>
    <p>{{name}}</p>
  </div>
</template>
<script>
import { ref } from "vue";

export default {
  setup() {
    const name = ref("Mike Jackson");    
    const nameClass=ref("nameClass");

    const onSubmit = () => {
      console.log(name.value);
    };
    
    return {
      name,
      onSubmit,    
      nameClass
    };
  },
};
</script>

<style>
.name {
  color: blue;
}
.name2 {
  color: red;
}
.nameClass{
  color:'gray';
}
</style>
