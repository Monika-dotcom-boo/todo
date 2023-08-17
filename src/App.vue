<template>
  <main class="w-[500px] max-w-full mx-auto">
    <TaskInput @onAddTask="addTasks"></TaskInput>
    <ul>
      <li v-for="item in taskList" :key="item.id">
        <TaskCard @onRemove="removeTask(item.id)" @onDone="setDoneTask(item.id)" :model="item"></TaskCard>
      </li>
    </ul>
  </main>
</template>

<script>
import TaskInput from "./components/TaskInput.vue";
import TaskCard from "./components/TaskCard.vue";
import {ref} from 'vue'

export default {
  name: 'App',
  components: {
    TaskCard,
    TaskInput
  },
  setup() {
    const taskList = ref([])
  
    const addTasks = ({title, description}) => {
      const generatedID = taskList.value.length <= 0 ? 1 : taskList.value[taskList.value.length - 1].id + 1;
      taskList.value = [...taskList.value, {id: generatedID, title, description, status: false}]
    }
  
    const setDoneTask = (id) => {
      taskList.value = taskList.value.map(x => {
        if(x.id === id)
          x.status = true
        return x 
      })
    }
  
    const removeTask = (id) => {
      taskList.value = taskList.value.filter(x => x.id !== id)
    }

    return {
      taskList, 
      addTasks, 
      removeTask, 
      setDoneTask
    }
  
  
  
  }

}
</script>

 