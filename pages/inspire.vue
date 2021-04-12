<template>
  <v-container >
    <v-row 
      no-gutters
      v-for="r in 6"
      :key="r"
    >
      <v-col
        v-for="n in 4"
        :key="n"
        cols="12"
        sm="3"
      >
      <v-card
        class="pa-2"
        outlined
        tile
      >
     <card></card>
      </v-card>

      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import card from '@/components/card.vue'
export default {
  
}
</script>
