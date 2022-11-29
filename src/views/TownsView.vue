<template>
  <v-container>
    <h1>Les Villes</h1>
    <v-row no-gutters>
      <v-col>
        <h3> <label for="filteractive">filtrage possible : </label><input type="checkbox" v-model="filterActive"
            id="filteractive">
          <div v-if="filterActive">
            <label for="filtertown">filtre : </label><input v-model="filter" id="filtertown">
          </div>
          <v-row v-for="(ville, id) in villesFiltre" :key="id"> 
            <v-col>
              {{ ville.nom }}
            </v-col>
            <v-col v-if="villesFiltre.length == 1">
              <v-row>
                <v-col>
                  Rues : {{ville.rues.length}}
                  <v-row>
                    <v-col>
                      <v-row v-for="(rue,id) in ville.rues" :key="id">
                        <v-col>
                          {{rue.nom}} : {{rue.boutiques.length}} boutiques
                        </v-col>
                        <v-col>
                          <v-row v-for="(boutique,id) in rue.boutiques" :key="id">
                            {{boutique.nom}} : {{boutique.itemStock.length}} en stock, {{boutique.itemCommande.length}} sur commande
                          </v-row>
                        </v-col>
                      </v-row>

                    </v-col>
                  </v-row>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
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
