<script>

export default {
  props: ["cards"],
}
</script>

<template>
  <div id="card0" class="col">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title" v-if="cards">{{cards[0]}}</h5>
        <img v-if="cards[3]" src="https://openweathermap.org/img/wn/02n.png" id="icone" class="img-fluid">
        <div class="temp">
          <span class="minima">{{cards[1]}} °C</span>
          <span class="maxima">{{cards[2]}} °C</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
* {
  color: white;
  font-size: 16px;
}

#card0,
.card {
  /* margin-top: 20%; */
  width: 100% !important;
  height: 90%;
}

#icone {
  width: 100px;
}

/* #card1{
    min-width: 500px !important;
} */

.col {
  padding-left: 7%;
  padding-right: 7%;
}

.card-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(75, 44, 89) !important;
}

.temp {
  width: 100%;
  display: flex;
  justify-content: space-around;
}

.minima,
.maxima {
  font-size: 25px;
}
</style>
