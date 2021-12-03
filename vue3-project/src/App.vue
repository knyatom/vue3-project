<template>
  <div>
    <div class="name">{{ name }}</div>
    <div>HI. Welcome</div>
    {{ greet }}
    <button class="btn btn-primary" v-on:click="consoleLog">Click</button>
    <button class="btn btn-primary" v-on:click="updateName">Update</button>
  </div>
</template>

<script>
export default {
  setup() {
    let name = "kim NY";
    const greeting = (name) => {
      return "Hello " + name;
    };
    const greet = greeting(name);
    const consoleLog = () => {
      console.log("Hello World");
    };
    const updateName = () => {
      name = "Kim Yu Na";
      console.log(name);
    };
    return {
      name,
      greet,
      consoleLog,
      updateName
    };
  },
};
</script>

<style>
.name {
  color: blue;
}
</style>
