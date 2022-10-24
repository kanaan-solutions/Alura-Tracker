<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <SideBar />
    </div>
    <div class="column is-three-quarter">
      <Formulary @savingTasks="saveTask" />
      <div class="list">
        <Task v-for="(task, index) in tasks" :key="index" :task="task" />
        <Box v-if="isListEmpty" >
          Você não está muito produtivo hoje :(
        </Box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
  import { defineComponent } from 'vue';
  import SideBar from './components/SideBar.vue';
  import Formulary from './components/Formulary.vue';
  import Task from './components/Task.vue'
  import ITask from './interfaces/ITask';
  import Box from './components/Box.vue';

  export default defineComponent({
      name: "App",
      components: { SideBar, Formulary, Task, Box },
      data () {
        return {
          tasks: [] as ITask[]
        }
      },
      computed: {
        isListEmpty (): boolean {
          return this.tasks.length ===0
        }
      }, 
      methods: {
        saveTask (tasks: ITask) {
          this.tasks.push(tasks)
        }
      }
  });
</script>

<style>
    .list {
        padding: 1.25rem;
    }
</style>
