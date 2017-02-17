<template>
  <div class="form">
    <template v-if="!editorMode">
      <button @click="addMode">Добавить</button>
    </template>
    <template v-else>
      <form @submit.prevent="addRow">
        <label for="name">Имя: <input type="text" id="name" v-model="profile.name" required></label>
        <label for="subname">Фамилия: <input type="text" id="subname" v-model="profile.subname" required></label>
        <label for="score">Оценка: <input type="number" id="score" max="10" min="1" v-model="profile.score" required></label>
      <div>
      <button type="submit">
        Добавить
      </button>
      <button @click="cancelMode" type="button">
        Отмена
      </button>
      </div>
      </form>
    </template>
  </div>
</template>

<script>
  export default {
    props: ['editorMode'],
    data () {
      return {
        profile: {}
      }
    },
    methods: {
      addMode () {
        this.$emit('changeMode', true)
      },
      cancelMode () {
        this.$emit('changeMode', false)
      },
      addRow (e) {
        this.$emit('addRow', Object.assign({}, this.profile))
        this.profile = {}
        this.$emit('changeMode', false)
      }
    }
  }
</script>


<style scoped>
  form {
    display: flex;
    justify-content: space-between;
  }
</style>
