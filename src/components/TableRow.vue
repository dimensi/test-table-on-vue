<template>
  <tr>
    <td>
      <template v-if="!modeEditor">
        {{ item.name }}
      </template>
      <template v-else>
        <input type="text" :value="item.name" v-model="item.name" required>
      </template>
    </td>
    <td>
      <template v-if="!modeEditor">
        {{ item.subname }}
      </template>
      <template v-else>
        <input type="text" :value="item.subname" v-model="item.subname" required>
      </template>
    </td>
    <td><Score v-for="(score, indexScore) in item.scores" :score="score" :indexScore="indexScore" :index="index" :modeEditor="modeEditor" /></td>
    <td>
      <Controls
      :modeEditor="modeEditor"
      :index="index"
      @backup="backup"
      @cancelObject="cancelObject"
      @save="save"
       /></td>
  </tr>
</template>

<script>
  import Score from './Score'
  import Controls from './Controls'
  export default {
    props: ['item', 'index'],
    components: {
      Score,
      Controls
    },
    data () {
      return {
        backupObject: {},
        modeEditor: false
      }
    },
    methods: {
      backup () {
        this.modeEditor = true
        this.backupObject = Object.assign({}, this.item)
      },
      save () {
        this.modeEditor = false
        const save = Object.assign({}, this.item)
        this.$emit('save', this.index, save)
      },
      cancelObject () {
        this.modeEditor = false
        this.$emit('cancel', this.index, this.backupObject)
      }
    }
  }
</script>
