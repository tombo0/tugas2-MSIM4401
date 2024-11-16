<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Coin Prices</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <CoinTable />
    </ion-content>
  </ion-page>
</template>

<script>
import CoinTable from "@/components/CoinTable.vue";

export default {
  components: {
    CoinTable,
  },
};
</script>
