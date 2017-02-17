<template>
  <div v-if="!modeEditor">
    <button @click="changeMode">Редактировать</button>
    <button @click="copy">Копировать</button>
  </div>
  <div v-else>
    <button @click="save">Сохранить</button>
    <button @click="cancel">Отменить</button>
  </div>
</template>


<script>
  export default {
    props: ['modeEditor', 'index'],
    methods: {
      copy () {
        this.$root.$emit('copy', this.index)
      },
      changeMode () {
        this.$emit('backup')
      },
      save () {
        this.$emit('save')
      },
      cancel () {
        this.$emit('cancelObject')
      }
    }
  }
</script>
