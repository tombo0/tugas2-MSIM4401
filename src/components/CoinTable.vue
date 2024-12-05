<template>
  <ion-card>
    <ion-card-header>
      <ion-button expand="full" @click="fetchData">Get Data</ion-button>
    </ion-card-header>
    <ion-card-content>
      <ion-grid>
        <!-- <ion-row>
          <ion-col><strong>Name</strong></ion-col>
          <ion-col><strong>Symbol</strong></ion-col>
          <ion-col><strong>Harga USD</strong></ion-col>
        </ion-row> -->
        <ion-row v-for="coin in coins" :key="coin.id">
          <ion-col id="coin-rank"><p class="col-header">Rank</p>{{ coin.rank }}</ion-col>
          <ion-col id="coin-symbol"><p class="col-header">{{ coin.name }}</p>{{ coin.symbol }}</ion-col>
          <ion-col id="coin-price-usd"><p class="col-header">USD</p>{{ coin.price_usd }}</ion-col>
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
ion-card {
  background-color: white;
}
ion-col {
  background-color: #fef7dc;
  text-align: center;
  color: black;
}
ion-row {
  border: 1px solid #c7c55a;
}
.col-header {
  font-size: 10px;
}
#coin-price-usd, #coin-symbol{
  text-align: left;
}
</style>
