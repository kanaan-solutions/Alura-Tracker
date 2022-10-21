<template>
    <div class="box has-text-weight-bold">
        <div class="column is-7">
            Descrição da tarefa
        </div>

        <div class="column">
            <Timer time=15 />
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue';
    import Timer from './Timer.vue'

    export default defineComponent({
        name: "Task",
        components: {
            Timer,
        }
    })
</script>

<style scoped>
    .box {
        background: #FAF0CA;
    }
</style>