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
                <CheckedList 
                    :data="shop.itemStock" 
                    :item-check="true"
                    :checked="Array(shop.itemStock.length).fill(false)"
                    :item-button="{ show: true, texte: 'acheter' }"
                    :list-button="{ show: true, texte: 'tout acheter' }" 
                    :fields="['nom', 'prix']" 
                    @list-button-clicked="lButnClkd"
                    @item-button-clicked="iButClkd" 
                    @checked-changed="cChangd">
                </CheckedList>
            </v-col>
            <v-col>
                <CheckedList 
                    :data="shop.itemCommande" 
                    :item-check="false"
                    :item-button="{ show: true, texte: 'commande' }"
                    :list-button="{ show: false}" 
                    :fields="['nom', 'prix']" 
                    @list-button-clicked="lButnClkd"
                    @item-button-clicked="iButClkd" 
                    @checked-changed="cChangd">
                </CheckedList>
            </v-col>

        </v-row>
    </div>
</template>
  
<script>
import CheckedList from '@/components/CheckedList.vue';
export default {
    name: 'ShopComponent',
    props: {
        shop: Object
    },
    components: {
        CheckedList
    }
}
</script>
  