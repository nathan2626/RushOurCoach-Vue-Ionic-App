<template>
  <ion-page>
    <ion-header :translucent="true" class="ion-no-border">
      <ion-toolbar>

        <ion-buttons slot="start">
          <ion-button>
            <ion-icon slot="end" :icon="gridOutline"></ion-icon>
          </ion-button>
        </ion-buttons>
        <ion-buttons slot="end">
          <ion-button>
            <ion-icon slot="start" :icon="search"></ion-icon>
          </ion-button>
        </ion-buttons>

      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div id="container">
        <!-- Content -->

      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonButtons, IonButton, IonIcon } from '@ionic/vue';
import { search, gridOutline } from 'ionicons/icons';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Reservation',
  components: {
    IonPage,
    IonHeader,
    IonToolbar,
    IonButtons,
    IonButton,
    IonIcon
  },
  setup() {
    return {
      search,
      gridOutline,
    }
  }
});
</script>

<style scoped>

ion-segment {
  margin: 0 10px;
}

ion-segment-button {
  text-transform: capitalize;
  transform: scale(.8, .8);
  --indicator-color: transparent;
  font-weight: 300;
  color: #fff;
}

ion-segment-button ion-label {
  position: relative;
  left: -17px;
  font-weight: bolder;
  font-size: 18px;
}

.segment-button-checked {
  color: #333;
}

.segment-button-checked:before {
  content: "";
  position: absolute;
  left: 0;
  bottom: 0;
  width: 50%;
  border-bottom: 4px solid #333;
}

ion-badge {
  padding: 8px 0;
  border-radius: 10px;
  color: #333;
  border: 1px solid #8c8c8c;
  box-shadow: 10px 9px 20px -1px rgba(0,0,0,0.49);
  -webkit-box-shadow: 10px 9px 20px -1px rgba(0,0,0,0.49);
  -moz-box-shadow: 10px 9px 20px -1px rgba(0,0,0,0.49);  width: 100%;
  text-align: center;
}

.poster-col {
  height: 26em;
}
.poster-col img {
  border-radius: 40px;
}

.rate {
  font-size: 14px;
  padding-top: 4px;
}

.rate ion-icon {
  color: gold;
}

h5 {
  margin-top: 4px;
  font-weight: 400;
  color: #fff;
}

p {
  font-size: 18px;
}

ion-buttons ion-button ion-icon {
  color: #fff;
}

/* Animations */
.swiper-slide-prev {
  opacity: .5;
  transform: rotate(-8deg);
}
.swiper-slide-next {
  opacity: .5;
  transform: rotate(8deg);
}
.swiper-slide {
  transition: .4s all;
}



</style>