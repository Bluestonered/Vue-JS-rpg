<template>
  <v-container>
    <h1>Les personnages</h1>

    <v-app>
      <v-row>
        <v-col>
          <h3>
            <label for="filterperso">filtre : </label><input v-model="filter" id="filtertown">
            <ul>
              <li v-for="(perso, index) in persoFiltre" :key="index">{{ perso.nom }}</li>
            </ul>
            <div v-if="persoFiltre.length === 1"></div>
          </h3>
        </v-col>
        <v-col>
          Attributs
        </v-col>
        <v-col>
          emplacements
        </v-col>
      </v-row>
    </v-app>
  </v-container>

</template>

<script>

import { mapState } from 'vuex'
export default {
  name: 'PersosView',
  data: () => ({
    filter: '',
    filterActive: false
  }),
  computed: {
    ...mapState(['persos']),
    persoFiltre() {
      return this.persos.filter(v => v.nom.includes(this.filter))
    }
  }

}
</script>