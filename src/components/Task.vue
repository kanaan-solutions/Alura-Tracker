<template>
    <Box>
        <div class="column is-7">
            {{ task.description || 'Tarefa sem descrição' }}
        </div>

        <div class="column">
            <Timer :time="task.durationInSeconds" />
        </div>
    </Box>
</template>

<script lang="ts">
    import ITask from '@/interfaces/ITask';
    import { defineComponent, PropType } from 'vue';
    import Timer from './Timer.vue'
    import Box from './Box.vue'

    export default defineComponent({
        name: "Task",
        components: {
            Timer,
            Box,
        },
        props: {
            task: {
                type: Object as PropType<ITask>,
                required: true,
            }
        }
    })
</script>