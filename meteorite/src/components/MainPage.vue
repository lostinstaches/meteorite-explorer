<template>
  <div>
    <search></search>
    <meteorite-table></meteorite-table>
  </div>
</template>

<script>
import Search from './Search'
import MeteoriteTable from './MeteoriteTable'

export default {
  name: 'MainPage',
  components: {Search, MeteoriteTable},
  data () {
    return {
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
