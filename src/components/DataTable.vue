<template>
  <div class="table">
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
        @cancel="changeObject"
        @save="changeObject"
        :key="index"
        />
      </tbody>
    </table>
    <AddForm
    :editorMode="addMode"
    @changeMode="changeMode"
    @addRow="addRow" />
  </div>
</template>

<script>
  import Vue from 'vue'
  import tableRow from './TableRow'
  import AddForm from './AddForm'
  export default {
    name: 'data',
    data () {
      return {
        addMode: false,
        thead: true,
        list: [
          {
            name: 'Иван',
            subname: 'Иванов',
            scores: [10, 9, 2]
          },
          {
            name: 'Илья',
            subname: 'Иванов',
            scores: [5, 6, 7]
          }
        ]
      }
    },
    components: {
      tableRow,
      AddForm
    },
    methods: {
      copy (index) {
        this.list.push(Object.assign({}, this.list[index]))
      },
      addRow (row) {
        this.list.push(row)
      },
      changeObject (index, object) {
        Vue.set(this.list, index, object)
      },
      increment (index, indexScore) {
        if (this.list[index].scores[indexScore] < 10) {
          const scores = [
            ...this.list[index].scores
          ]
          scores[indexScore]++
          Vue.set(this.list, index, Object.assign({}, this.list[index], this.list[index].scores[indexScore]++))
        }
      },
      decrement (index, indexScore) {
        if (this.list[index].scores[indexScore] > 1) {
          const scores = [
            ...this.list[index].scores
          ]
          scores[indexScore]--
          Vue.set(this.list, index, Object.assign({}, this.list[index], {
            scores
          }))
        }
      },
      changeMode (mode) {
        this.addMode = mode
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
.form,
.table {
  max-width: 1000px;
  margin: 0 auto;
}

.data {
  width: 100%;
  text-align: center;
  margin-bottom: 20px;
}

th:nth-child(1),
th:nth-child(2) {
  width: 25%
}

th:nth-child(3) {
  width: 20%
}
</style>
