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

                  Boutiques
                </v-card>
              </v-col>
              <v-col>
                <v-card class="pa-2" outlined tile v-for="(ville, index) in villesFiltre" :key="index">
                  Rues: {{ ville.rues.length }}
                </v-card>
              </v-col>
            </v-row>
            <v-row no-gutters>
              <v-col v-for="(ville, index) in villesFiltre" :key="index">
                <v-row>
                  <v-card class="pa-2" outlined tile v-for="(rue, indexRue) in ville.rues" :key="indexRue">
                    {{ rue.nom }} : {{ rue.boutiques.length }} boutiques

                    <v-col v-for="(shop, indexShop) in rue.boutiques" :key="indexShop">
                      {{ shop.nom }} : {{ shop.itemStock.length }} articles en stock, {{ shop.itemCommande.length }} sur
                      commande
                    </v-col>
                  </v-card>
                </v-row>

              </v-col>

              <!-- <v-col v-for="(ville, index) in villesFiltre" :key="index">
                <v-card class="pa-2" outlined tile v-for="(rue, indexRue) in ville.rues" :key="indexRue">
                  <v-row v-for="(shop, indexShop) in rue.boutiques" :key="indexShop">

                    {{ shop.nom }} : {{ shop.itemStock.length }} articles en stock, {{ shop.itemCommande.length }} sur
                    commande

                  </v-row>
                  {{ rue.nom }} : {{ rue.boutiques.length }} boutiques
                </v-card>
              </v-col> -->

            </v-row>

            <v-row>
              <v-col v-for="(ville, index) in villesFiltre" :key="index"> Rues: {{ ville.rues.length }}</v-col>
              <v-col> Boutiques</v-col>
            </v-row>
            <v-row>
              <v-col v-for="(ville, index) in villesFiltre" :key="index">
                <v-card class="pa-2" outlined tile v-for="(rue, indexRue) in ville.rues" :key="indexRue">
                  {{ rue.nom }} : {{ rue.boutiques.length }} boutiques
                </v-card>
              </v-col>
              <v-col> Boutiques</v-col>
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
