<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <div class="header">
        <h2>Transactions</h2>
      </div>
      <div class="segment">
        <ion-segment @ionChange="segmentChanged($event)" :value="$data.subview">
          <ion-segment-button value="in">
            <ion-label>In-flow</ion-label>
          </ion-segment-button>
          <ion-segment-button value="out">
            <ion-label>Out-flow</ion-label>
          </ion-segment-button>
        </ion-segment>
      </div>


      <div class="transactions">
        <!-- transaction in flow -->
        <div class="tr-body" v-if="subview == 'in'">
          <ion-list>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 1.300.000</ion-label>
              <ion-label>Pokémon Yellow</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 120.000</ion-label>
              <ion-label>Mega Man X</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 1.100.000</ion-label>
              <ion-label>Pac-Man</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 500.000</ion-label>
              <ion-label>Pokémon Yellow</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 200.000</ion-label>
              <ion-label>Mega Man X</ion-label>
            </ion-item>
          </ion-list>
        </div>

        <!-- transaction out flow -->

        <div class="tr-body" v-if="subview == 'out'">
          <ion-list>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>The Legend of Zelda</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Pac-Man</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Pokémon Yellow</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Mega Man X</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>The Legend of Zelda</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Pac-Man</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Super Mario World</ion-label>
            </ion-item>
          </ion-list>
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonPage, IonList, useBackButton, useIonRouter, IonLabel, IonSegment, IonSegmentButton, IonIcon, IonItem } from '@ionic/vue';
import { arrowDownCircleOutline, arrowUpCircleOutline } from 'ionicons/icons';

export default {
  components: {
    IonContent,
    IonPage,
    IonList,
    IonLabel,
    IonSegment,
    IonSegmentButton,
    IonIcon,
    IonItem
  },
  data() {
    return {
      subview: 'in',
    }
  },
  setup() {
    const ionRouter = useIonRouter();
    useBackButton(-1, () => {
      if (!ionRouter.canGoBack()) {
        App.exitApp();
      }
    });

    return {
      ionRouter,
      useBackButton,
      arrowDownCircleOutline,
      arrowUpCircleOutline
    }
  },
  methods: {
    segmentChanged(sel) {
      this.subview = sel.detail.value
      console.log(sel)
    }
  },
}
</script>

<style scoped>
/* background */
ion-content {
  --background: rgb(245, 245, 245);
}

.header h2 {
  text-align: center;
  color: #000000;
  font-size: 1.5em;
  font-family: 'Poppins-Medium';
}

.segment ion-segment {
  width: 60%;
  margin: 0 auto 1em;
  background-color: #ffffff;
  border-radius: .5em;
}

ion-segment-button::part(indicator-background) {
  background: #08a391;
}

ion-label {
  font-family: 'Poppins-SemiBold';
}

/* Material Design styles */
ion-segment-button.md::part(native) {
  color: #000;
}

.segment-button-checked.md::part(native) {
  color: #08a391;
}

ion-segment-button.md::part(indicator-background) {
  height: 4px;
}

/* iOS styles */
ion-segment-button.ios::part(native) {
  color: #08a391;
  font-family: 'Poppins-SemiBold';
  font-weight: 700;
}

.segment-button-checked.ios::part(native) {
  color: #fff;
}

ion-segment-button.ios::part(indicator-background) {
  border-radius: .5em;
}


/* transaction list in */
.transactions {
  /* height: 100vh; */
  border-top-left-radius: 2em;
  border-top-right-radius: 2em;
  /* position: relative; */
  width: 100%;
  margin: 2em auto 0;
  padding-bottom: 18em;
  background: rgb(222, 222, 222);
}

ion-list {
  background: transparent;
  margin-top: 3em;
}

.tr-body ion-icon {
  transform: rotate(40deg);
  font-size: 3em;
  padding: 10px;
}

.tr-body ion-label {
  font-size: 1.2em;
}
</style>
