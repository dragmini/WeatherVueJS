<template>
    <div class="cards">
        <CardCity v-for="(card, index) in this.cards" :key="index" :card="card" :index="index" :cardsLenght="cardsLenght"></CardCity>
        <!-- <button @click="this.getDataWeather"></button> -->
        <!-- <div>
            {{ this.searchText }}
        </div> -->
    </div>
</template>

<style>
.cards {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    height: 50%;
    align-items: flex-end;
    /* margin-top: 7%; */
}
</style>

<script>
import CardCity from './CardCity.vue'
// import Vue from 'vue'

// Vue.forceUpdate();
// import HeaderMenu from './HeaderMenu.vue'

const TOKEN = 'cac8f5b67a00d4b4cb1c5f18d2c23b22'

export default {
    props: ['searchText'],
    watch: {
        searchText(newVal) {
            if(this.newVal !== '') {
            this.getDataWeather(newVal)
            }
        }
    },
    data() {
        return {
            cards: [],
            cardsLenght: 0,
            startCard: [
                {
                    cityName: 'Moscow',
                },
                {
                    cityName: 'London',
                },
                {
                    cityName: 'New York',
                },
                {
                    cityName: 'Dubai',
                },
            ]
        }
    },
    components: {
        CardCity
    },
    mounted() {
        this.loadStartCity()
    },
    methods: {
        loadStartCity() {
            this.startCard.map((card) => {
                    this.getDataWeather(card.cityName)
                })
        },
        getDataWeather(cityName) {
            fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cityName}&appid=${TOKEN}`)
                .then(response => response.json())
                .then(data => {
                        this.saveDataWeather(data)
                        
                    });
        },
        saveDataWeather(data) {
            this.cards.splice(this.cards.length/2, 0, data)
            // this.cardsLenght = this.cards.length
            this.cardsLenght++
            // Vue.forceUpdate();
        },
    }
}

</script>
