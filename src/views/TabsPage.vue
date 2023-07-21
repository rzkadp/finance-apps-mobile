<template>
  <ion-page>
    <ion-tabs>
      <ion-router-outlet></ion-router-outlet>
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="home" href="/tabs/home">
          <ion-icon aria-hidden="true" :icon="homeOutline" />
        </ion-tab-button>

        <ion-tab-button tab="transactions" href="/tabs/transactions">
          <ion-icon aria-hidden="true" :icon="pieChartOutline" />
        </ion-tab-button>

        <ion-tab-button tab="card" href="/tabs/card">
          <ion-icon aria-hidden="true" :icon="cardOutline" />
        </ion-tab-button>

        <ion-tab-button tab="settings" href="/tabs/settings">
          <ion-icon aria-hidden="true" :icon="settingsOutline" />
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script setup lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { pieChartOutline, homeOutline, cardOutline, settingsOutline } from 'ionicons/icons';
</script>

<style scoped>
ion-tabs {
  background: rgb(222, 222, 222);
}

ion-tabs ion-tab-bar {
  position: relative;
  width: 90%;
  transform: translate(-50%, -50%);
  left: 50%;
  border-radius: 30px;
  padding-bottom: 0;
  border: 1px solid rgba(2, 52, 54, 0.88);
  overflow: hidden;
  box-shadow: 0px -5px 10px rgb(3 181 170 / 8%);
  height: 80px;
  background: var(--ion-color-light);
}

ion-tab-button {
  --background: var(--ion-color-light);
  --color: #BEC2C6;
}

ion-tab-button ion-icon {
  font-size: 1.9rem;
}
</style>