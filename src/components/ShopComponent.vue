<template>
    <div>
        <v-row>
            {{ shop.nom }}
        </v-row>
        <v-row>
            <v-col>
                Stock: {{ shop.itemStock.length }} items
            </v-col>
            <v-col>
                Sur commande : {{ shop.itemCommande.length }}
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <CheckedList :data="shop.itemStock" :item-check="true"
                    :checked="Array(shop.itemStock.length).fill(false)" :item-button="{ show: true, texte: 'acheter' }"
                    :list-button="{ show: true, texte: 'tout acheter' }" :fields="['nom', 'prix']"
                    @list-button-clicked="lButnClkd" @item-button-clicked="iButClkd" @checked-changed="cChangd">
                </CheckedList>
            </v-col>
            <v-col>
                <CheckedList :data="shop.itemCommande" :item-check="false"
                    :item-button="{ show: true, texte: 'commande' }" :list-button="{ show: false }"
                    :fields="['nom', 'prix']" @list-button-clicked="lButnClkd" @item-button-clicked="iButClkd"
                    @checked-changed="cChangd">
                </CheckedList>
            </v-col>

        </v-row>





        <v-dialog
        :value="dialog"
        width="500"
      >
  
        <v-card>
          <v-card-title class="text-h5 grey lighten-2">
            Privacy Policy
          </v-card-title>
  
          <v-card-text>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </v-card-text>
  
          <v-divider></v-divider>
  
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary"
              text
              @click="dialog = false"
            >
              I accept
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

    </div>


</template>
  
<script>
import CheckedList from '@/components/CheckedList.vue';
export default {
    name: 'ShopComponent',
    data: () => ({
    dialog: false,
  }),
    props: {
        shop: Object,

    },
    components: {
        CheckedList
    },
    methods: {

        iButClkd(id) {
            this.dialog = true;
            console.log(id);
        }
    }
}
</script>
  