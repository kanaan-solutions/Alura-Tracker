<template>
    <div class="box has-text-weight-bold">
        <div class="column is-7">
            {{ task.description }}
        </div>

        <div class="column">
            <Timer :time="task.durationInSeconds" />
        </div>
    </div>
</template>

<script lang="ts">
    import ITask from '@/interfaces/ITask';
import { defineComponent, PropType } from 'vue';
    import Timer from './Timer.vue'

    export default defineComponent({
        name: "Task",
        components: {
            Timer,
        },
        props: {
            task: {
                type: Object as PropType<ITask>,
                required: true,
            }
        }
    })
</script>

<style scoped>
    .box {
        background: #FAF0CA;
    }
</style>