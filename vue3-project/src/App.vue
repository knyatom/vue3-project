<template>
  <div v-bind:class="nameClass">
    <div class="name">{{ name }}- {{ name2 }}</div>
    <div>HI. Welcome</div>
    {{ greet }}
    <button class="btn btn-primary" v-on:click="consoleLog">Click</button>
    <button class="btn btn-primary" v-on:click="updateName">Update</button>
    <br />
    <input type="text" v-bind:value="name" />
    <input v-bind:type="type" v-bind:value="name" />
  </div>
</template>
<script>
import { ref } from "vue";
import { reactive } from "vue";

export default {
  setup() {
    const name = ref("Kim NY Welcome");
    const name2 = reactive({ id: 1 });
    const type = ref("text");
    const nameClass = ref("name");
    const consoleLog = () => {
      console.log("Hello World");
      name.value = "Hello";
      name2.id = "KIM";
       nameClass.value = "name";
    };

    const updateName = () => {
      name.value = "Kim Yu Na";
      name2.id = "Welcome";
      type.value = "number";
      nameClass.value = "name2";
      console.log(name.value);
    };
    return {
      name,
      consoleLog,
      updateName,
      name2,
      type,
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
</style>
