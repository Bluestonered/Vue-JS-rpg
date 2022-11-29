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
            
          </h3>
        <div v-if="persoFiltre.length === 1">
          <v-row v-for="(perso, index) in persoFiltre" :key="index">
          <v-col>
            <v-row>
              Attributs
            </v-row>
            <v-row>
              Niveau :{{ perso.level }}
            </v-row>
            <v-row>
              Vie :{{ perso.nom }}
            </v-row>
            <v-row>
              Vitalité :{{ perso.nom }}
            </v-row>
            <v-row>
              Force :{{ perso.nom }}
            </v-row>
            <v-row>
              Armure :{{ perso.nom }}
            </v-row>
            <v-row>
              Or :{{ perso.nom }}
            </v-row>
          </v-col>
          
          <v-col>
            <v-row>
              emplacements
            </v-row>
            <v-row>
              tête :{{ perso.level }}
            </v-row>
            <v-row>
              Corps :{{ perso.nom }}
            </v-row>
            <v-row>
              Mains :{{ perso.nom }}
            </v-row>
            <v-row>
              Ceinture :{{ perso.nom }}
            </v-row>
            <v-row>
              Sac a dos :{{ perso.nom }}
            </v-row>
            <v-row>
              item acheté :{{ perso.nom }}
            </v-row>
          </v-col>


        </v-row>
        
        
        </div>
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