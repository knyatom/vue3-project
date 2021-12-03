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
    const name = "kim NY";
    const greeting = (name) => {
      return "Hello " + name;
    };
    const greet = greeting(name);
    return {
      name,
      greet,
    };
  },
};
</script>

<style>
.name {
  color: blue;
}
</style>
