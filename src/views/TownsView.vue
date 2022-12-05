<template>
  <v-container>
    <h1 class="center">Les Villes</h1>
    <v-row no-gutters>
      <v-col>
        <h3> <label for="filteractive">filtrage possible : </label><input type="checkbox" v-model="filterActive"
            id="filteractive">
          <div v-if="filterActive">
            <label for="filtertown">filtre : </label><input v-model="filter" id="filtertown">
          </div>
          <div v-else>
            <ul>
              <li v-for="(ville, index) in villes" :key="index">{{ ville.nom }}</li>
            </ul>
          </div>
          <v-row v-for="(ville, id) in villesFiltre" :key="id">
            <v-col>
              <div v-if="filterActive">
                {{ ville.nom }}
              </div>



              <div v-if="villesFiltre.length == 1">


                <v-row v-for="(rue, id) in ville.rues" :key="id">
                  <br>
                  <br>
                  <button v-on:click="myFunction(id)">
                    <span class="button_top"> {{ rue.nom }}
                    </span>
                  </button>
                  <div v-if="(idRue == id)">
                  <CheckedList :data="rue.boutiques" :item-check="false"
                    :item-button="{ show: true, texte: 'Selectionner' }"
                    :list-button="{ show: false, texte: 'biscuit' }" :fields="['nom']" @list-button-clicked="lButnClkd"
                    @item-button-clicked="iButClkd" @checked-changed="cChangd"></CheckedList>

                    
                  </div>
                  <v-col>
                    <div v-if="(idRue == id)">
                    <Shop :name-shop="rue.boutiques[idSlctshop].nom"></Shop>
                 
                  </div>
                </v-col>
                  
                </v-row>
              </div>


            </v-col>
            <v-col v-if="villesFiltre.length == 1">
              <v-row>

                <v-col>
                  Rues : {{ ville.rues.length }}
                  <v-row>
                    <v-col>
                      <v-row v-for="(rue, id) in ville.rues" :key="id">
                        <v-col>
                          {{ rue.nom }} : {{ rue.boutiques.length }} boutiques
                        </v-col>
                        <v-col>
                          <v-row v-for="(boutique, id) in rue.boutiques" :key="id">
                            {{ boutique.nom }} : {{ boutique.itemStock.length }} en stock, {{
    boutique.itemCommande.length
                            }}
                            sur commande
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
import CheckedList from '@/components/CheckedList.vue';
import Shop from '@/components/ShopComponent.vue';
export default {
  name: 'TownsView',
  data: () => ({
    filter: '',
    filterActive: false,
    idRue: -1,
    idSlctshop: 0,
  }),
  computed: {
    ...mapState(['villes']),
    villesFiltre() {
      return this.villes.filter(v => v.nom.includes(this.filter))
    }
  },
  components: {
    CheckedList,
    Shop
  },
  methods: {

    myFunction(id){
      this.idRue = id;
    },

    iButClkd(id){
      this.idSlctshop = id;
    }
}

}
</script>

<style scoped>
.center {
  align-content: center;
  justify-content: center;
  text-align: center;
}

button {
  /* Variables */
  --button_radius: 0.85em;
  --button_color: #e8e8e8;
  --button_outline_color: #000000;
  font-size: 17px;
  font-weight: 0px;
  border: none;
  border-radius: var(--button_radius);
  background: var(--button_outline_color);
  margin: 5px 0;
  padding: 0px;
  width: 90%;
}

.button_top {
  display: block;
  box-sizing: border-box;
  border: 2px solid var(--button_outline_color);
  border-radius: var(--button_radius);
  padding: 0.75em 1.5em;
  background: var(--button_color);
  color: var(--button_outline_color);
  transform: translateY(-0.2em);
  transition: transform 0.1s ease;
}

button:hover .button_top {
  /* Pull the button upwards when hovered */
  transform: translateY(-0.33em);
}

button:active .button_top {
  /* Push the button downwards when pressed */
  transform: translateY(0);
}
</style>
