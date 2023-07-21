<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <!-- label top -->
      <div id="circle-background"></div>
      <div class="topbar">
        <!-- <h1>Cards</h1> -->

      </div>

      <!-- top container -->
      <swiper :modules="modules" :slides-per-view="1" :space-between="50" @swiper="onSwiper" @slideChange="onSlideChange"
        :pagination="{
          clickable: true,
        }">
        <swiper-slide>
          <div class="container">
            <div class="head-content">
              <img src="../assets/images/mastercard.png" alt="mastercard">
            </div>
            <div class="body-content">
              <p class="head-information">8744 9022 4758 6778</p>
              <p class="foot-information">Rizky Adi Pratama</p>
            </div>
            <div class="footer-content">
              <p>08/24</p>
            </div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="container">
            <div class="head-content">
              <img src="../assets/images/mastercard.png" alt="mastercard">
              <p>Total Balance</p>
            </div>
            <div class="body-content">
              <p class="head-information"><ion-icon :icon="logoEuro"></ion-icon> 100.000.00</p>
              <p class="foot-information">Rizky Adi Pratama</p>
            </div>
            <div class="footer-content">
              <p>08/24</p>
            </div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="container">
            <div class="head-content">
              <img src="../assets/images/mastercard.png" alt="mastercard">
              <p>Total Balance</p>
            </div>
            <div class="body-content">
              <p class="head-information"><ion-icon :icon="logoEuro"></ion-icon> 100.000.00</p>
              <p class="foot-information">Rizky Adi Pratama</p>
            </div>
            <div class="footer-content">
              <p>08/24</p>
            </div>
          </div>
        </swiper-slide>
      </swiper>

      <div class="transactions">
        <div class="tr-label">
          <h2>Transactions</h2>
        </div>
        <div class="tr-body">
          <ion-list>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Pokémon Yellow</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Mega Man X</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowUpCircleOutline" color="danger"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>The Legend of Zelda</ion-label>
            </ion-item>
            <ion-item color="none" lines="none">
              <ion-icon :icon="arrowDownCircleOutline" color="success"></ion-icon>
              <ion-label>Rp. 100.000</ion-label>
              <ion-label>Pac-Man</ion-label>
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

<script setup lang="ts">
import { IonContent, IonPage, IonIcon, useBackButton, useIonRouter } from '@ionic/vue';
import { arrowDownCircleOutline, arrowUpCircleOutline, logoEuro } from 'ionicons/icons';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { App } from '@capacitor/app';

// Import Swiper styles
import 'swiper/css';
import 'swiper/css/pagination';

// import required modules
import { Pagination } from 'swiper/modules';

const onSwiper = (swiper) => {
  console.log(swiper);
};
const onSlideChange = () => {
  console.log('slide change');
};
const modules = [Pagination]

const ionRouter = useIonRouter();
useBackButton(-1, () => {
  if (!ionRouter.canGoBack()) {
    App.exitApp();
  }
});
</script>

<style scoped>
/* background */
#circle-background {
  position: absolute;
  margin: 7em 0 0 -8em;
  border-radius: 50%;
  width: 300px;
  height: 300px;
  background-color: rgb(85, 203, 142);
}

/* head label */
.topbar {
  text-align: center;
}

.topbar h1 {
  color: #ffffff;
  font-size: 1.5em;
  font-family: 'Poppins-Medium';
}

/* top card container */
.container {
  color: #ffffff;
  margin: 2em auto;
  box-shadow: 0 0 3px #ffffff;
  width: 90%;
  height: 16em;
  border-radius: 2.5em;
  backdrop-filter: blur(12px);
}

.head-content {
  font-size: 2em;
  padding-top: 1em;
  padding-left: 1em;
}

.head-content img {
  width: 1.2em;
}

.head-content p {
  font-size: .5em;
  text-align: center;
  margin-top: -2em;
}

.body-content {
  position: fixed;
  width: 100%;
}

.body-content .head-information {
  font-size: 1.6em;
  font-family: 'Poppins-SemiBold';
  margin-top: .5em;
  text-align: center;
  /* background-color: blue; */
}

.body-content .foot-information {
  font-size: 1.2em;
  font-family: 'Poppins-Light';
  text-align: center;
  /* background-color: red; */
  margin-top: -1em;
}

.footer-content p {
  position: fixed;
  bottom: 1em;
  margin-left: 2em;
  font-size: 1em;
  font-family: 'Poppins-Medium';
}


.transactions {
  border-top-left-radius: 2em;
  border-top-right-radius: 2em;
  position: absolute;
  width: 100%;
  margin: 7em auto 0;
  padding-bottom: 8em;
  background: rgb(222, 222, 222);
}

.tr-label h2 {
  font-family: 'Poppins-SemiBold';
  margin-top: 2em;
  margin-left: 2em;
  font-size: 1.2em;
}

ion-list {
  background: transparent;
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
