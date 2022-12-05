<template>
  <div>
    <v-card style="max-width: 50rem;" v-for="(item, id) in data" :key="id">
      <v-card-text>
        <v-row>
          <v-checkbox @click="$emit('checked-changed', id)" v-if="itemCheck" :checked="checked[id]" ></v-checkbox>
          <v-col class="justify-space-between" v-for="field in fields" :key="field">
            {{ item[field] }}
          </v-col>
          <v-btn @click="$emit('item-button-clicked', id)" v-if="(itemButton.show)" tile color="success">
          {{ itemButton.texte }}
          </v-btn>
        </v-row>
      </v-card-text>
    </v-card>
    <v-row v-if="(listButton.show)" justify="center">
      <v-btn @click="$emit('list-button-clicked', id)" tile color="error">
        {{ listButton.texte }}
      </v-btn>
    </v-row>
  </div>
</template>
<script>

export default {
  name: 'CheckedList',
  props: {
    data: Array, // les données sources
    fields: Array, // le tableau contenant le nom des champs
    itemCheck: Boolean, // s'il y a des case à cocher
    checked: Array, // le tableau des cases cochées
    itemButton: Object, // l'objet pour les boutons d'items
    listButton: Object, // l'objet pour le bouton de liste
  },
  data: () => {
    return {


    }
  },

  methods: {
  }
}

</script>
  
<style scoped>



</style>