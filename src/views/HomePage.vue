<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <!-- label top -->
      <div id="circle-background"></div>
      <div class="header">
        <div class="name">
          <h2>Hi, Rizky Adi Pratama</h2>
        </div>
        <div class="image">
          <img src="../assets/images/profile.png" alt="profile">
        </div>
      </div>

      <!-- top container -->
      <div class="container">
        <swiper :modules="modules" :slides-per-view="1" :space-between="50" @swiper="onSwiper"
          @slideChange="onSlideChange" :pagination="{
            clickable: true,
          }">
          <swiper-slide>
            <div class="head-content">
              <img src="../assets/images/visa.png" alt="visa">
              <p>Total Balance</p>
            </div>
            <div class="body-content">
              <p class="head-information"><ion-icon :icon="logoEuro"></ion-icon> 100.000.00</p>
              <p class="foot-information">Rizky Adi Pratama</p>
            </div>
            <div class="footer-content">
              <p>08/24</p>
            </div>
          </swiper-slide>
          <swiper-slide>
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
          </swiper-slide>
        </swiper>
      </div>

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
import { IonContent, IonPage, IonIcon, useBackButton, useIonRouter, IonLabel, IonItem, IonList } from '@ionic/vue';
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
  margin: 2em 0 0 15em;
  border-radius: 50%;
  width: 300px;
  height: 300px;
  background-color: rgb(85, 203, 142);
}

/* header */
.header {
  position: relative;
  margin-top: -.5em;
  /* top: 0; */
  height: 2em;
  margin-bottom: 4em;
  /* background-color: red; */
}

.header .name {
  margin-left: 1.5em;
  padding-top: .5em;
}

.header .name h2 {
  color: white;
  font-family: 'Poppins-Medium';
  font-size: 1.2em;
}

.header .image {
  box-shadow: 0 0 10px #f8f8f8;
  margin: -2.5em 1em 0 0;
}

.header .image img {
  position: relative;
  width: 3em;
  float: right;
}

/* top card container */
.container {
  color: #ffffff;
  margin: 2em auto;
  box-shadow: 0 0 3px #ffffff;
  width: 90%;
  /* max-height: 16em; */
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
  width: 100%;
}

.body-content .head-information {
  font-size: 2.5em;
  font-family: 'Poppins-SemiBold';
  margin-top: .5em;
  text-align: center;
}

.body-content .foot-information {
  font-size: 1.2em;
  font-family: 'Poppins-Light';
  text-align: center;
  margin-top: -1.5em;
}

.footer-content {
  padding-bottom: 1em;
}

.footer-content p {
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
