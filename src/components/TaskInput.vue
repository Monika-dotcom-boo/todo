<template>
    <div class="m-2.5 flex 	place-content: space-around;">
      <input class="rounded border border-solid border-1x lightgrey p-2.5" v-model="title" placeholder="Title" type="text">
      <input class="rounded border border-solid border-1x lightgrey p-2.5" v-model="description" placeholder="Description" type="text">
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
    setup(props, { emit}) {
        const title = ref('')
        const description = ref('')
  
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
  

  