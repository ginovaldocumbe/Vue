<script>
import top from "./top.vue"
import foote from "./footer.vue"
import cards from "./cards.vue"

export default {
  name: "Inicio",
  components: {
    top,
    foote,
    cards
  },
  data() {
    return {
      cidades: [
        "Maputo",
        "Xai-Xai",
        "Inhambane",
        "Beira",
        "Chimoio",
        "Tete",
        "Quelimane",
        "Nampula",
        "Pemba",
      ],
      cards1: [],
      cards2: [],
      cards3: [],
      interval: null,
      controlador: 0,
    };
  },
  methods: {
    weather() {
      if (this.controlador == 9) {
        this.controlador = 0;
        fetch(
          "https://api.openweathermap.org/data/2.5/weather?q=Lichinga,MZ&units=metric&APPID=423a905a8694371beac028a0e861eabb"
        )
          .then((resp) => resp.json())
          .then((data) => {
            this.cards1[0] = data.name;
            this.cards1[1] = data.main.temp_min;
            this.cards1[2] = data.main.temp_max;
            this.cards1[3] = data.weather[0].icon;
            this.cards1[4] = data.weather[0].main;
            console.log(data)
          })
          .catch((err) => console.log(err));
      } else {
        this.controlador = this.controlador + 3;
        for (let a = this.controlador - 3; a < this.controlador; a++) {
          fetch(
            "https://api.openweathermap.org/data/2.5/weather?q=" +
            this.cidades[a] +
            ",MZ&units=metric&APPID=423a905a8694371beac028a0e861eabb"
          )
            .then((resp) => resp.json())
            .then((data) => {
              console.log(data)
              if (a == 0 || a == 3 || a == 6) {
                this.cards1[0] = data.name;
                this.cards1[1] = data.main.temp_min;
                this.cards1[2] = data.main.temp_max;
                this.cards1[3] = data.weather[0].icon;
                this.cards1[4] = data.weather[0].main;
              } else if (a == 1 || a == 4 || a == 7) {
                this.cards2[0] = data.name;
                this.cards2[1] = data.main.temp_min;
                this.cards2[2] = data.main.temp_max;
                this.cards2[3] = data.weather[0].icon;
                this.cards2[4] = data.weather[0].main;
              } else if (a == 2 || a == 5 || a == 8) {
                this.cards3[0] = data.name;
                this.cards3[1] = data.main.temp_min;
                this.cards3[2] = data.main.temp_max;
                this.cards3[3] = data.weather[0].icon;
                this.cards3[4] = data.weather[0].main;
              }
            })
            .catch((err) => console.log(err));
        }
      }
    },
  },
  mounted() {
    this.weather();
  },
  created() {
    this.interval = setInterval(() => {
      this.weather();
    }, 4000);
  },
};
</script>

<template>
  <div class="custom-shape-divider-top-1662394809">
    <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
      <path d="M1200 120L0 16.48 0 0 1200 0 1200 120z" class="shape-fill"></path>
    </svg>
  </div>
  <section>
    <top />
    <div class="cd">
      <cards :cards ="cards1"/>
      <cards :cards ="cards2" />
      <cards :cards ="cards3"/>
    </div>
    <foote class="ter"/>
  </section>
</template>

<style>
section {
  display: flex;
  padding-top: 10%;
  height: 100vh;
  overflow-y: scroll;
  flex-direction: column;
  justify-content: space-between !important;
  align-items: center;
}
.ter{
  bottom: 0;
  position: fixed;
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


