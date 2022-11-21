<template>
  <v-container>
    <h1>Les personnages</h1>



    <v-app>
      <v-card class="text-h6 ma-10" outlined>
        <v-row align="center" no-gutters>
          <v-col cols="12" sm="2" class="d-flex justify-center align-center text-center pa-5">
            <h3>
              <label for="filterperso">filtre : </label><input v-model="filter" id="filtertown">
              <ul>
                <li v-for="(perso, index) in persoFiltre" :key="index">{{ perso.nom }}</li>
              </ul>
            </h3>
          </v-col>
          <v-divider inset vertical class="d-none d-sm-block"></v-divider>
          <v-divider inset class="d-block d-sm-none"></v-divider>
          <v-col cols="12" sm="2" class="d-flex justify-center align-center text-center pa-5">
            <h3>
              <div v-if="persoFiltre.length === 1">Two</div>
            </h3>
          </v-col>
        </v-row>
      </v-card>
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