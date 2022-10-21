<template>
  <div class="box">
    <div class="colu mn">
      <div class="is-flex is-align-items-center is-justify-content-space-between">
        <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
          <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
        </div>

        <div class="column">
          <Clock />
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
      components: {
        Clock
      },
      data () {
        return {
          time: 0,
          timer: 0,
        }
      },
      
      methods: {
        start () {
          this.timer = setInterval(() => {
            this.time += 1
          }, 1000)
        },
        stop () {
          clearInterval(this.timer)
        }
      }
  })
</script>