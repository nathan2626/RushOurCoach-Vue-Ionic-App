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
        <h1>Annulation</h1>
        <div class="ion-padding">

          <form action="" class="ion-padding">

            <input type="hidden" name="token">

            <div style="display: flex; justify-content: space-around; align-items: center">
              <label class="label" for="cgu">
                J'ai lu et accepté les <a href="#">conditions d'utilisation</a>
              </label>
              <input class="" type="checkbox" checked id="cgu" name="cgu" required>
            </div>


            <div class="container-form-btn ion-padding-top">
              <button class="form-btn custom-font">
                Annuler
              </button>
            </div>

          </form>

        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonPage, IonHeader, IonToolbar, IonButtons, IonButton, IonIcon } from '@ionic/vue';
import { search, gridOutline } from 'ionicons/icons';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Annulation',
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

h1 {
  text-align: center;
  margin-top: 5rem;
}

.wrap-input {
  background-color: rgba(255, 255, 255, .5);
  border-radius: 20px;
  margin-bottom: 26px;
  box-shadow: 0 10px 30px 0 rgba(57,71,82, 0.12);
}

.input {
  display: block;
  width: 100%;
  background: transparent;
  font-size: 16px;
  line-height: 1.2;
  border: none;
  outline: none;
  height: 46px;
  padding: 0 20px 0 23px;
  color: #000;
}

.label a {
  color: #000;
  text-decoration: none;
}
.label {
  font-size: 0.9em;
}

.container-form-btn {
  display: flex;
  justify-content: center;
}

.form-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 20px;
  min-width: 160px;
  height: 42px;
  background-color: #455EF7;
  border-radius: 20px;
  font-size: 14px;
  color: #fff;
  text-transform: uppercase;
  margin-top: 50px;
  transition: all .4s;
  box-shadow: 0 10px 30px 0 rgba(57,71,82, 0.5);
}

.form-btn:hover {
  background-color: #fff;
  color: #455EF7;
  box-shadow: 0 10px 30px 0 rgba(57,71,82, 0.8);
}

ion-buttons ion-button ion-icon {
  color: #fff;
}

/* Animations */




</style>