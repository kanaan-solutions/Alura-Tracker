<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="Logo">
    </h1>7
    <button class="button" @click="changeTheme">
      {{ buttonText }}
    </button>
  </header>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'

  export default defineComponent({
      name: "SideBar",
      emits: ["changedTheme"],
      data () {
        return {
          darkModeActive: false
        }
      },
      computed: {
        buttonText () {
          if(this.darkModeActive) {
            return "Desativar Modo Escuro"
          }
          return "Ativar Modo Escuro"
        }
      },
      methods: {
        changeTheme() {
          this.darkModeActive = !this.darkModeActive
          this.$emit('changedTheme', this.darkModeActive)
        }
      }
  })
</script>

<style scoped>
  header {
    padding: 1rem;
    background: #0d3b66;
    width: 100%;
    height: 100vh;
    text-align: center;
  }

  @media only screen and (max-width: 768px) {
    header {
      padding: 2.5rem;
      height: auto;
    }
  }
</style>