<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <!-- label top -->
      <div id="circle-background"></div>
      <div id="top-label">
        <h1>Cards</h1>
      </div>

      <!-- top container -->
      <div id="top-container">
        <swiper :modules="modules" :slides-per-view="1" :space-between="50" @swiper="onSwiper"
          @slideChange="onSlideChange" :pagination="{
            clickable: true,
          }">
          <swiper-slide>
            <div class="head-swiper">
              <img src="../assets/images/mastercard.png" alt="mastercard">
            </div>
            <div class="body-swiper">
              <p class="number-card">8744 9022 4758 6778</p>
              <p class="name">Rizky Adi Pratama</p>
            </div>
            <div class="footer-swiper">
              <p>08/24</p>
            </div>
          </swiper-slide>
          <swiper-slide>
            <div class="head-swiper">
              <img src="../assets/images/mastercard.png" alt="mastercard">
            </div>
            <div class="body-swiper">
              <p class="number-card"><ion-icon :icon="logoEuro"></ion-icon> 100.000.00</p>
              <p class="name">Rizky Adi Pratama</p>
            </div>
            <div class="footer-swiper">
              <p>01/25</p>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonPage, IonIcon, useBackButton, useIonRouter } from '@ionic/vue';
import { logoEuro } from 'ionicons/icons';
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
#top-label {
  text-align: center;
}

#top-label h1 {
  color: #ffffff;
  font-size: 1.5em;
  font-family: 'Poppins-Medium';
}

/* top card container */
#top-container {
  color: #ffffff;
  margin: 2em auto;
  box-shadow: 0 0 3px #ffffff;
  width: 90%;
  height: 16em;
  border-radius: 2.5em;
  backdrop-filter: blur(12px);
}

.head-swiper {
  font-size: 2em;
  padding-top: 1em;
  padding-left: 1em;
}

.head-swiper img {
  width: 1.2em;
}

.body-swiper {
  width: 100%;
}

.body-swiper .number-card {
  font-size: 1.6em;
  font-family: 'Poppins-SemiBold';
  margin-top: .5em;
  text-align: center;
  /* background-color: blue; */
}

.body-swiper .name {
  font-size: 1.2em;
  font-family: 'Poppins-Light';
  text-align: center;
  /* background-color: red; */
  margin-top: -1em;
}

.footer-swiper p {
  /* position: fixed; */
  bottom: 1em;
  margin-left: 2em;
  font-size: 1em;
  font-family: 'Poppins-Medium';
}

/* emoney style */
#emoney {
  border-radius: 1em;
  position: relative;
  margin: 2em auto 0;
  width: 96%;
  height: 8em;
  /* background-color: #ffffff; */
}

#emoney #card {
  padding: .4em;
  background-color: #ffffff;
  border-radius: 1em;
  /* width: 6em; */
  height: 6em;
}

#card img {
  display: block;
  margin: 2em auto;
  width: 80%;
  /* background-color: red; */
  /* width: 100px; */
  /* height: 100px; */
  /* object-fit: cover; */
}
</style>
