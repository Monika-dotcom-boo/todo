<template>
    <div class="flex rounded border border-solid border-[lightgrey] p-2.5 justify-between items-center m-2.5">
        <div class="flex flex-col p-2.5">
            <h4 class="font-bold">{{ model.title }}</h4>
            <p>{{ model.description }}</p>
        </div>
        <div>
            <button class="p-2.5 " @click="emitOnDone" v-if="!model.status">✅</button>
            <button class="p-2.5" @click="emitOnRemove" v-else>❌</button>
        </div>
    </div>
</template>

<script>
    export default{
        emits: ['onDone', 'onRemove'],
        props: {
            model: {
            required: true,
            default: {
                id: 0,
                title: 'Create video',
                description: 'And upload on YouTube',
                status: false
                }
            }
        },  
        setup(props, { emit }) {
            const emitOnDone = () => {
            emit('onDone')
        }
            const emitOnRemove = () => {
            emit('onRemove')
            }
        return {
            emitOnDone,
            emitOnRemove
            }
        }
     }
</script>
