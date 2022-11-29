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
                  Niveau :{{ perso.niveau }}
                </v-row>
                <v-row>
                  Vie :{{ perso.attributs.vie }}
                </v-row>
                <v-row>
                  Vitalité :{{ perso.attributs.vitalite }}
                </v-row>
                <v-row>
                  Force :{{ perso.attributs.force }}
                </v-row>
                <v-row>
                  Armure :{{ perso.attributs.protection }}
                </v-row>
                <v-row>
                  Or :{{ perso.or }}
                </v-row>
              </v-col>

              <v-col>
                <v-row>
                  emplacements
                </v-row>
                <v-row>

                  <ul>
                    <li v-for="(emplacement, index) in perso.emplacements" :key="index">
                      {{ emplacement.nom }}
                      <span v-if="emplacement.items.length !== 0">
                        [{{ emplacement.items.length }}] : <span v-for="(item, indexItem) in emplacement.items"
                          :key="indexItem">{{ item.nom }}, </span>
                      </span>
                    </li>
                  </ul>

                </v-row>
                <v-row>
                  item acheté :{{ perso.itemsAchetes.length }}
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
    },
  }

}
</script>