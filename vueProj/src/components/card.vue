<script>

export default {
    props: ["cards"],
};

</script>

<template>
    <div id="todos" class="row row-cols-1 row-cols-md-3 g-4">
        <div id="card0" class="col">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title" v-if="cards">{{cards[0] }}</h5>
                    <img src="" id="icone" class="img-fluid">
                    <div class="temp">
                        <span class="minima">10</span>
                        <span class="maxima">10 °C</span>
                    </div>
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