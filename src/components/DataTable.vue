<template>
  <table class="data" >
    <thead v-if="thead">
      <tr>
        <th>Имя</th>
        <th>Фамилия</th>
        <th>Оценка</th>
        <th>Действия</th>
      </tr>
    </thead>
    <tbody>
      <table-row
      v-for="(item, index) in list"
      :item="item"
      :index="index"
      @copy="copy"
      @increment="increment"
      @decrement="decrement"
      :key="index"
      />
    </tbody>
  </table>
</template>

<script>
  import tableRow from './TableRow'
  export default {
    name: 'data',
    data () {
      return {
        message: 'Таблица',
        thead: true,
        list: [
          {
            name: 'Иван',
            subname: 'Иванов',
            score: '10'
          },
          {
            name: 'Илья',
            subname: 'Иванов',
            score: '5'
          }
        ]
      }
    },
    components: {
      tableRow
    },
    methods: {
      copy (index) {
        this.list.push(this.list[index])
      },
      increment (index) {
        this.list[index].score >= 10 ? false : this.list[index].score++
      },
      decrement (index) {
        this.list[index].score <= 1 ? false : this.list[index].score--
      }
    },
    mounted () {
      this.$root.$on('copy', this.copy)
      this.$root.$on('increment', this.increment)
      this.$root.$on('decrement', this.decrement)
    }
  }
</script>

<style scoped>
.data {
  max-width: 1000px;
  margin: 0 auto;
  width: 100%;
}
</style>
