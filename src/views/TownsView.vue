<template>
  <v-container>
    <h1>Les Villes</h1>


    <v-card class="text-h6 ma-10" outlined>
      <v-row align="center" no-gutters>
        <v-col cols:="12" sm="2" class="d-flex justify-center align-center text-center pa-5">
          <h3> <label for="filteractive">filtrage possible : </label><input type="checkbox" v-model="filterActive"
              id="filteractive">
            <div v-if="filterActive">
              <label for="filtertown">filtre : </label><input v-model="filter" id="filtertown">

              <ul>
                <li v-for="(ville, index) in villesFiltre" :key="index">{{ ville.nom }}</li>
              </ul>
            </div>
            <div v-else>
              <ul>
                <li v-for="(ville, index) in villes" :key="index">{{ ville.nom }}</li>
              </ul>

            </div>
          </h3>
        </v-col>
        <v-divider inset vertical class="d-none d-sm-block"></v-divider>
        <v-divider inset class="d-block d-sm-none"></v-divider>
        <v-col cols:="12" sm="2" class="d-flex justify-center align-center text-center pa-5">
          <h3>
            <div v-if="villesFiltre.length === 1">Two</div>
          </h3>
        </v-col>
      </v-row>
    </v-card>

  </v-container>




</template>

<script>

import { mapState } from 'vuex'
export default {
  name: 'TownsView',
  data: () => ({
    filter: '',
    filterActive: false,
    nbr: 0
  }),
  computed: {
    ...mapState(['villes']),
    villesFiltre() {
      return this.villes.filter(v => v.nom.includes(this.filter))
    }
  }

}
</script>
