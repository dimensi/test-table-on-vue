<template>
  <div class="score">
    <button @click="decrement" v-if="modeEditor">-</button>
    <div class="text">{{ counter }}</div>
    <button @click="increment" v-if="modeEditor">+</button>
  </div>
</template>

<script>
  export default {
    props: ['score', 'index', 'indexScore', 'modeEditor'],
    computed: {
      counter () {
        return this.score
      }
    },
    methods: {
      increment () {
        this.$root.$emit('increment', this.index, this.indexScore)
      },
      decrement () {
        this.$root.$emit('decrement', this.index, this.indexScore)
      }
    }
  }
</script>

<style scoped>
  .score {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin: 0 auto 5px;
  }
  .text {
    width: 30px;
  }
  button {
    border: 1px solid black;
    background-color: transparent;
    border-radius: 2px;
    cursor: pointer;
    font-size: 20px;
    width: 30px;
    height: 30px;
    margin: 0 10px
  }
</style>
