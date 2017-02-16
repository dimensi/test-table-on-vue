<template>
  <tr>
    <td>{{ item.name }}</td>
    <td>{{ item.subname}}</td>
    <td><Score :score="item.score" :index="index" /></td>
    <td><Controls :saveMode="false" :index="index" /></td>
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
    }
  }
</script>
