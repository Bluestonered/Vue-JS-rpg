<template>
  <v-container>
    <h1>Les Villes</h1>
    <v-row no-gutters>
      <v-col :cols="2">
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
      <v-col :cols="10">
        <h3>
          <div v-if="villesFiltre.length === 1">
            <v-row no-gutters>
              <v-col order="last">
                <v-card class="pa-2" outlined tile>

                  Boutique
                </v-card>
              </v-col>
              <v-col>
                <v-card class="pa-2" outlined tile v-for="(ville, index) in villesFiltre" :key="index">
                  Rues: {{ ville.rues.length }}
                </v-card>
              </v-col>
            </v-row>
            <v-row no-gutters>
              <v-col order="last">
                <v-card class="pa-2" outlined tile>

                  Boutique 1
                  Boutique 2
                </v-card>
              </v-col>
              <v-col>
                <v-card class="pa-2" outlined tile>
                  Rue + Nbr Boutique
                </v-card>
              </v-col>
            </v-row>
            <v-row no-gutters>
              <v-col order="last">
                <v-card class="pa-2" outlined tile>
                  Boutique 1
                  Boutique 2
                </v-card>
              </v-col>
              <v-col>
                <v-card class="pa-2" outlined tile>

                  Rue2 + Nbr Boutique
                </v-card>
              </v-col>
            </v-row>

          </div>
        </h3>
      </v-col>
    </v-row>
  </v-container>




</template>

<script>

import { mapState } from 'vuex'
export default {
  name: 'TownsView',
  data: () => ({
    filter: '',
    filterActive: false,
  }),
  computed: {
    ...mapState(['villes']),
    villesFiltre() {
      return this.villes.filter(v => v.nom.includes(this.filter))
    }
  }

}
</script>
