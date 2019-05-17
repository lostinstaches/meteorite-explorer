<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
<v-card>
  <v-data-table
    :headers="headers"
    :items="meteorites"
    ></v-data-table>
  <template v-slot:items="props">
    <td>{{props.item.id}}</td>
    {{items}}
  </template>
  {{meteorites}}
</v-card>
</template>

<script>
export default {
  name: 'Table',
  data () {
    return {
      headers: [
        {
          text: 'id',
          align: 'left',
          sortable: false,
          value: 'id'
        }],
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
