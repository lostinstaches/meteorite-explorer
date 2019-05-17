<template>
<h1>{{meteorites}}</h1>
</template>

<script>
export default {
  name: 'Table',
  data () {
    return {
      meteorites: []
    }
  },
  created () {
    var apiURL = 'https://data.nasa.gov/resource/gh4g-9sfh.json'
    fetch(apiURL)
      .then(res => res.json())
      .then(res => (this.meteorites = res))
      // eslint-disable-next-line handle-callback-err
      .catch(error => console.log())
  }

}
</script>

<style scoped>

</style>
