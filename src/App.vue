<template>
  <div id="app">
    <img src="./assets/logo.png">
    <data-table></data-table>
  </div>
</template>

<script>
import DataTable from './components/DataTable'

export default {
  name: 'app',
  components: {
    DataTable
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input,
button {
  display: inline-block;
  padding: 4px 8px;
  border: 1px solid;
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;
  line-height: 1.25;
  -webkit-user-select: none;
  user-select: none;
  border-radius: .25em;
  font-size: 16px;
  font-weight: 500;
  transition: .3s;
  background: 0 0;
  cursor: pointer
}

input {
  cursor: auto
}
</style>
