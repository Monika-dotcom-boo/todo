<template>
    <div>
        <div class="flex justify-between items-center grid-rows-auto auto-cols-max gap-0 rounded border: solid 1px lightgrey p-2.5">
            <h4>{{ model.title }}</h4>
            <p>{{ model.description }}</p>
        </div>
        <div>
            <button class="rounded border border-solid border-1x lightgrey p-2.5" @click="emitOnDone" v-if="!model.status" >✅</button>
            <button class="rounded border border-solid border-1x lightgrey p-2.5" @click="emitOnRemove" v-else>❌</button>
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
     };
</script>
