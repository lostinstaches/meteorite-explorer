<template>
  <div>
    <div class="nav">
      <div class="icon">Icon</div>
      <h2>Navigation</h2>
      <div class="search">Search</div>
    </div>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Table</h2>
  </div>
  </div>
</template>

<script>
export default {
  name: 'MainPage',
  data () {
    return {
      msg: 'Welcome to Your Meteorite Explorer'
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
