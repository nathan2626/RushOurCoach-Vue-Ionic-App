<template>

  <div class="ion-padding">
    <form @submit.prevent="sendReservation" method="" action="" class="ion-padding">

      <input type="hidden" name="token">

      <div class="wrap-input">
        <input placeholder="Date" v-model="dateInput" class="input" type="date" id="date_select" name="date_select" >
      </div>

      <div class="wrap-input">
        <input placeholder="Heure" v-model="hourInput"  type="time" id="hour_select" class="input" name="hour_select" min="09:00" max="18:00" step="3600" >
      </div>

      <div class="wrap-input">
        <input placeholder="Email" v-model="emailInput"  type="email" class="input" id="email" name="email" >
      </div>

      <div style="display: flex; justify-content: space-around; align-items: center">
        <label class="label" for="cgu">
          J'ai lu et accepté les <a href="#">conditions d'utilisation</a>
        </label>
        <input class="" v-model="cguInput" type="checkbox" checked id="cgu" name="cgu" >
      </div>


      <div v-if="displayButton === true" class="container-form-btn ion-padding-top">
        <button class="form-btn custom-font">
          Réserver
        </button>
      </div>
      <div v-else style="display: none;">
      </div>

    </form>

    <div v-if="tokenWhenSend" class="container-form-btn ion-padding-top">
      <a class="form-btn noDecoration custom-font" :href="'/reservation/annulation/'+ tokenWhenSend">
        Annuler
      </a>
    </div>

  </div>

</template>

<script>
import axios from "axios";

export default  {
  name: 'Reservation',
  data () {
    return {
      resultError: "",
      tokenWhenSend: "",
      displayButton: true,
      resultStatus: "",
      emailInput: "",
      dateInput: "",
      hourInput: "",
      cguInput: true,
      thisToken: ""
    }
  },
  components: {

  },
  methods: {
    displayMessage(msg, type){
      const toast = document.createElement('ion-toast');
      toast.message = msg;
      toast.duration = 5000;
      toast.color = type;
      document.body.appendChild(toast);
      return toast.present();
    },
    sendReservation() {
      this.thisToken = Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);

      console.log(this.thisToken, this.emailInput, this.hourInput, this.dateInput, this.cguInput)

      const reservation = {
        email: `${this.emailInput}`,
        date_select: `${this.dateInput}`,
        hour_select: `${this.hourInput}`,
        cgu: `${this.cguInput}`,
        token: `${this.thisToken}`
      };

      axios
          .post(
              `http://rushourcoach.herokuapp.com/api/reservation`, reservation
          )
          .then((response) => {
            this.resultStatus = response.data;
            this.$bus.emit("resultStatus", this.resultStatus);

            this.displayMessage(`${this.resultStatus.status}`, "success")
            this.tokenWhenSend = this.resultStatus.token;
            this.displayButton = false;

            console.log(response.data)
          })
          .catch((error) => {
            this.resultError = error.response.data.errors;
            this.$bus.emit("resultError", this.resultError);

            if(Object.values(this.resultError).length > 1){
              this.displayMessage(`Plusieurs champs du formualaire n'ont pas été remplis..`, "danger")

            } else {
              this.displayMessage(`${Object.values(this.resultError)}`, "danger")
            }


            console.log(Object.values(this.resultError));
          })
    }
  },
  setup() {
    return {

    }
  }
}
</script>

<style scoped>

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

.noDecoration {
  text-decoration: none;
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

</style>