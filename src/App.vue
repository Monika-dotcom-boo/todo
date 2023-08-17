<template>
  <main>
    <TaskCard></TaskCard>
    <TaskImput></TaskImput>
  </main>
</template>

<script>
import TaskInput from "./components/TaskInput.vue";
import TaskCard from "./components/TaskCard.vue";

export default {
  name: 'App',
  components: {
    TaskCard,
    TaskInput,
    TaskImput
},
  setup() {

  }

  }
</script>

 