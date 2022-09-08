<script >
import Header from "./header.vue";
import Card from "./card.vue";
import Footer from "./footer.vue";

export default {
  name: 'Principal',
  data() {
    return {
      prov: ["Maputo", "Xai-Xai", "Inhambane", "Beira", "Chimoio", "Nampula", "Lichinga", "Tete", "Quelimane", "Pemba"],
      prov1: [],
      prov2: [],
      prov3: [],
      interval: null,
      controlador: 0,
    };
  },
  components: {
    Header,
    Footer,
    Card
  },
  methods: {
    renew() {
      if (this.controlador == 10) {
        this.controlador = 0;
        apiKey: "423a905a8694371beac028a0e861eabb";
        fetch(
          "https://api.openweathermap.org/data/2.5/weather?q=Maputo&units=metric&appid="
          + this.apiKey
        )
          .then((response) => response.json())
          .then((data) => {
            this.prov1[0] = data.name;
            this.prov1[1] = data.main.emp_min;
            this.prov1[2] = data.main.temp_max;
            this.prov1[3] = data.weather.weather[0].icon;
            this.prov1[4] = data.weather[0].description;

          })
          .catch((err) => console.log(err));
      } else {
        this.controlador = this.controlador + 3;
        alert("Teste")
        for (let a = this.controlador - 3; a < this.controlador; a++) {
          fetch(
            "https://api.openweathermap.org/data/2.5/weather?q=Mozambique,MZ&units=metric&APPID=423a905a8694371beac028a0e861eabb"
          )
            .then((resp) => resp.json())
            .then((data) => {

              if (a == 0 || a == 3 || a == 6) {

                this.prov1[0] = data.name;
                this.prov1[1] = data.main.temp_min;
                this.prov1[2] = data.main.temp_max;
                this.prov1[3] = data.weather.weather[0].icon;
                this.prov1[4] = data.weather[0].description;

              } else if (a == 1 || a == 4 || a == 7) {
                this.prov2[0] = data.name;
                this.prov2[1] = data.main.temp_min;
                this.prov2[2] = data.main.temp_max;
                this.prov2[3] = data.weather.weather[0].icon;
                this.prov2[4] = data.weather[0].description;
              } else if (a == 2 || a == 5 || a == 8) {
                this.prov3[0] = data.name;
                this.prov3[1] = data.main.temp_min;
                this.prov3[2] = data.main.temp_max;
                this.prov3[3] = data.weather.weather[0].icon;
                this.prov3[4] = data.weather[0].description;
              }
            })
            .catch((err) => console.log(err));
        }
      }
    },
  },
};





// let weather = {
//     apiKey: "423a905a8694371beac028a0e861eabb",
//     fetchWeather: function (cidade) {
//         fetch(
//             "https://api.openweathermap.org/data/2.5/weather?q="
//             +cidade
//             +"&units=metric&appid="
//             +this.apiKey
//         )
//             .then((response) => response.json())
//     .then((data) => this.displayW(data));
//     },
//   }

    // displayW : function(data,id){
    //   const {name} = data;
    //   const {icon, description} = data.weather[0];
    //   const {temp_min,temp_max}= data.main;
    //   console.log("Esse e um teste "+name,icon,description);
    //   document.querySelector(".card-body :nth-child(1)").innerText= name;
    //   document.querySelector("#icone").src= "https://openweathermap.org/img/wn/"+icon+".png";
    //   document.querySelector(".minima").innerText= temp_min+" °C";
    //   document.querySelector(".maxima").innerText= temp_max+" °C";
    // }
// }; 


</script>

<template>
  <div class="custom-shape-divider-top-1662394809">
    <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M1200 120L0 16.48 0 0 1200 0 1200 120z" class="shape-fill"></path>
    </svg>
  </div>
  <section>
    <Header />
    <div class="cd">
      <Card :cards="prov1" />
      <Card :cards="prov2" />
      <Card :cards="prov3" />
    </div>
    <Footer />
  </section>
</template>

<style scoped>
section {
  display: flex;
  padding-top: 10%;
  height: 100vh;
  flex-direction: column;
  justify-content: space-between !important;
  align-items: center;
}

.cd {
  display: flex;
  padding-top: 50px;
  flex-direction: column;
  width: 100%;
  height: 100%;
}

.custom-shape-divider-top-1662394809 {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  line-height: 0;
  z-index: -1;
}

.custom-shape-divider-top-1662394809 svg {
  position: relative;
  display: block;
  width: calc(300% + 1.3px);
  height: 400px;
  transform: rotateY(180deg);
}

.custom-shape-divider-top-1662394809 .shape-fill {
  fill: #2c032c;
}

@media only screen and (min-width: 768px) {
  .cd {
    display: flex;
    flex-direction: row;
  }
}
</style>
