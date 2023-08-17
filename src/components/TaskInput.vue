<template>
    <div class="m-2.5 flex flex-wrap">
      <input class="rounded border border-solid border-[lightgrey] p-2.5 w-full  mb-3" v-model="title" placeholder="Title" type="text">
      <input class="rounded border border-solid border-[lightgrey] p-2.5 w-full mb-3" v-model="description" placeholder="Description" type="text">
      <button class="rounded border border-solid border-[lightgrey] p-2.5 w-full bg-gray-400 mb-3" @click="onAddTask">Add task</button>
    </div>
</template>
  
<script>
import { ref } from 'vue' 

export default {
  emits: ['onAddTask'],
    setup(props, { emit}) {
        const title = ref('')
        const description = ref('')
  
        const onAddTask = () => {
          if(title.value === '' || description.value === '') {
            alert('Fill some info please!')
            return false
          }
          emit('onAddTask', { title: title.value, description: description.value })
          title.value = '';
          description.value = ''
        }   
      return {
        title,
        description,
        onAddTask
     }
    }
  }
  </script>
  

  