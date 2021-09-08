<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="py-4 d-flex justify-center">
        <img
          src="../assets/NT.png"
          width="40%"
        >
      </v-card>
      <v-card>
        <v-card-title class="headline">
          歡迎使用此模板
        </v-card-title>
        <v-card-text>
          <p>這個模板是根據Nuxt.js的基礎改進而成的，歡迎各位使用。但對於圖像等非程式碼的使用本團隊保有最終解釋權</p>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/introUs"
          >
            關於我們
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>
