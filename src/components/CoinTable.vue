<template>
  <ion-card>
    <ion-card-header>
      <ion-button expand="full" @click="fetchData">Get Data</ion-button>
    </ion-card-header>
    <ion-card-content>
      <ion-grid>
        <ion-row>
          <ion-col><strong>Name</strong></ion-col>
          <ion-col><strong>Symbol</strong></ion-col>
          <ion-col><strong>Harga USD</strong></ion-col>
        </ion-row>
        <ion-row v-for="coin in coins" :key="coin.id">
          <ion-col>{{ coin.symbol }}</ion-col>
          <ion-col>{{ coin.name }}</ion-col>
          <ion-col>{{ coin.price_usd }}</ion-col>
        </ion-row>
      </ion-grid>
    </ion-card-content>
  </ion-card>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      coins: [], // Tempat menyimpan data koin
    };
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get("https://api.coinlore.net/api/tickers/");
        this.coins = response.data.data; // Ambil data koin dari API
      } catch (error) {
        console.error("Error fetching data:", error);
      }
    },
  },
};
</script>

<style scoped>
ion-card {
  margin: 16px;
}
ion-button {
  margin-bottom: 16px;
}
</style>
