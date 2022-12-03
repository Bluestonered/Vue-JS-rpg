<template>
    <div>
            <v-row>
                {{NameShop}}
            </v-row>
            <v-row>
                <v-col>
                    STOCK
                </v-col>
                <v-col>
                    Sur commande
                </v-col>
            </v-row>
            <v-row>
                <v-col>
                    uishfiuhsdiu
                </v-col>
                <v-col>
                    ghioghdfoigfd
                </v-col>

            </v-row>
    </div>
</template>
  
<script>
export default {
    name: 'ShopComponent',
    props: {
        NameShop: String,
    }
}
</script>
  