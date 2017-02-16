<template>
  <div class="score">
    <button @click="decrement">-</button>
    <div class="text">{{ counter }}</div>
    <button @click="increment">+</button>
  </div>
</template>

<script>
  export default {
    props: ['score', 'index'],
    computed: {
      counter () {
        return this.score
      }
    },
    methods: {
      increment () {
        this.$root.$emit('increment', this.index)
      },
      decrement () {
        this.$root.$emit('decrement', this.index)
      }
    }
  }
</script>

<style scoped>
  .score {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 100px;
    width: 100%;
    margin: 0 auto;
  }

  button {
    border: 1px solid black;
    background-color: transparent;
    border-radius: 2px;
    cursor: pointer;
    font-size: 20px;
    width: 30px;
    height: 30px;
  }
</style>
