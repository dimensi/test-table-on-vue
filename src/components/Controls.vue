<template>
  <div v-if="!saveMode">
    <button>Редактировать</button>
    <button @click="copy">Копировать</button>
  </div>
  <div v-else>
    <button>Сохранить</button>
    <button>Отменить</button>
  </div>
</template>


<script>
  export default {
    props: ['saveMode', 'index'],
    methods: {
      copy () {
        console.log('copy item')
        this.$root.$emit('copy', this.index)
      }
    }
  }
</script>
