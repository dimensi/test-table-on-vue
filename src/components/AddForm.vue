<template>
  <div class="form">
    <template v-if="!editorMode">
      <button @click="addMode">Добавить</button>
    </template>
    <template v-else>
      <form @submit.prevent="addRow">
        <label for="name">Имя: <input type="text" id="name" v-model="profile.name" required></label>
        <label for="subname">Фамилия: <input type="text" id="subname" v-model="profile.subname" required></label>
        <label for="score1">Оценка: <input type="number" id="score1" max="10" min="1" v-model="profile.scores[0]" required></label>
        <label for="score2">Оценка: <input type="number" id="score2" max="10" min="1" v-model="profile.scores[1]" required></label>
        <label for="score3">Оценка: <input type="number" id="score3" max="10" min="1" v-model="profile.scores[2]" required></label>
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
        profile: {
          scores: []
        }
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
