<template>
  <div class="box form">
    <div class="colu mn">
      <div class="is-flex is-align-items-center is-justify-content-space-between">
        <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
          <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="description">
        </div>

        <div class="column">
          <Clock @timerFinished="taskFinished" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  import Clock from "./Clock.vue"

  export default defineComponent({
      name: 'Formulary',
      emits: ["savingTasks"],
      components: {
        Clock
      },
      data () {
        return {
          description: ''
        }
      },
      
      methods: {
        taskFinished (timePassed: number): void {
          this.$emit('savingTasks', {
            durationInSeconds: timePassed,
            description: this.description,
          })
          this.description = ''
        },
      }
  })
</script>

<style>
  .form {
    color: var(--text-primary);
    background-color: var(--bg-primary);
  }
</style>