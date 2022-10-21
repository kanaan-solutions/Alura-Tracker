<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Timer :time="time" /> 

    <button class="button" @click="start" :disabled="timerStart" >
      <span class="icon">
      <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="stop" :disabled="!timerStart">
      <span class="icon">
      <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  import Timer from "./Timer.vue"

  export default defineComponent({
      name: 'Formulary',
      emits: ['timerFinished'],
      components: {
        Timer
      },
      data () {
        return {
          time: 0,
          timer: 0,
          timerStart: false,
        }
      },
      
      methods: {
        start () {
          this.timerStart = true,
          this.timer = setInterval(() => {
            this.time += 1
          }, 1000)
        },
        stop () {
          this.timerStart = false
          clearInterval(this.timer)
          this.$emit('timerFinished', this.time)
          this.time = 0
        }
      }
  })
</script>