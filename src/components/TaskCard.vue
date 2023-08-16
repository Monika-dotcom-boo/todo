<template>
    <div>
        <div class="task-card my-style">
            <h4>{{ model.title }}</h4>
            <p>{{ model.description }}</p>
        </div>
        <div>
            <button v-if="!model.status">OK</button>
            <button v-else>USUŃ</button>
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
        setup( ){
            
        }
    }
</script>

<style scoped>

</style>