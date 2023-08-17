<template>
    <div class="task-input">
      <imput v-model="title" placeholder="Title" type="text"></imput>
      <imput v-model="description" placeholder="Description" type="text"></imput> 
      <button @click="onAddTask">Add task</button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue' 

export default {
  emits: {
    onAddTask({ title, description }) { 
      if(title === '' || description === '') {
        alert('Fill some info please!')
        return false
      }
      return true
    }
  },
    setup() {
        const title = ref( value: '')
        const description = ref( value: '')
  
        const onAddTask = () => {
            emit('onAddTask', { title: title.value, description: description.value })
        }   
      return {
        title,
        description,
        onAddTask
     }
    }
  }
  </script>
  

  