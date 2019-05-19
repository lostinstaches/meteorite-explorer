<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <div id="app">
    <v-app id="inspire">
      <v-flex xs10 offset-xs1>
      <v-card>
        <v-card-title>
          Meteorite Explorer
          <v-spacer></v-spacer>
          <v-text-field
            v-model="search"
            append-icon="search"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        </v-card-title>
        <v-data-table
          :headers="headers"
          :items="meteorites"
          :search="search"
        >
          <template v-slot:items="props">
            <td>{{ props.item.name }}</td>
            <td class="text-xs-right">{{ props.item.id }}</td>
            <td class="text-xs-right">{{ props.item.nametype }}</td>
            <td class="text-xs-right">{{ props.item.recclass }}</td>
            <td class="text-xs-right">{{ props.item.mass }}</td>
            <td class="text-xs-right">{{ props.item.fall }}</td>
            <td class="text-xs-right">{{ props.item.year.substring(0,4) }}</td>
            <td class="text-xs-right">{{ props.item.reclat }}</td>
            <td class="text-xs-right">{{ props.item.reclong }}</td>
          </template>
          <template v-slot:no-results>
            <v-alert :value="true" color="error" icon="warning">
              Your search for "{{ search }}" found no results.
            </v-alert>
          </template>
        </v-data-table>
      </v-card>
      </v-flex>
    </v-app>
  </div>
</template>

<script>
export default {
  name: 'Table',
  data () {
    return {
      search: '',
      headers: [
        {
          text: 'Name',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: 'ID', sortable: false, value: 'id' },
        { text: 'NameType', sortable: false, value: 'nametype' },
        { text: 'Rec Class', sortable: false, value: 'recclass' },
        { text: 'Mass (g)', sortable: false, value: 'mass' },
        { text: 'Fall', sortable: false, value: 'fall' },
        { text: 'Year', sortable: false, value: 'year' },
        { text: 'Latitude', sortable: false, value: 'reclat' },
        { text: 'Longitute', sortable: false, value: 'reclong' }
      ],
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
