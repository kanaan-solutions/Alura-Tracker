<template>
  <div class="box">
    <div class="colu mn">
      <div class="is-flex is-align-items-center is-justify-content-space-between">
        <div class="column is-8" role="form" aria-label="Formulário para a criação de uma nova tarefa">
          <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
        </div>
        <section>
          <strong>{{ timePassed }}</strong>
        </section>
        <button class="button" @click="start">
          <span class="icon">
            <i class="fas fa-play"></i>
          </span>
          <span>play</span>
        </button>
        <button class="button" @click="stop">
          <span class="icon">
            <i class="fas fa-stop"></i>
          </span>
          <span>stop</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
      name: 'Formulary',
      data () {
        return {
          time: 0
        }
      },
      computed: {
        timePassed () : string {
          return new Date(this.time * 1000).toISOString().substr(11,8) 
        }
      },
      methods: {
        start () {
          setInterval(() => {
            this.time += 1
          }, 1000)
        },
        stop () {
          console.log("stop")
        }
      }
  })
</script>