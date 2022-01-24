<template>
    <div class="card">
        <!-- <img class="image-icon-weather"> -->
        <div v-bind:id="index" class="card-ground">
            <p class="name">{{ this.card.name }}, {{ this.card.sys.country }}</p>
            <div class="information">
                <div class="option-day-temp">
                    <div class="option-temp">
                        <h3 class="temp" v-if="this.card.main.temp">{{ Math.round(this.card.main.temp -273.15) }}</h3>
                        <p class="temp-icon">°C</p>
                    </div>
                    <p class="date">{{ this.formatDataTime() }}</p>
                </div>
                <div class="condition-weather">
                    <p v-for="(weather, index) in this.card.weather" :key="index" v-bind:class="weather.main">{{ weather.main }}</p>
                </div>
            </div>
        </div>
        <button class="view-stats">VIEW STATS</button>
    </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Alegreya+Sans:wght@500&display=swap');

.card {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 85%;
    width: 15%;
}
.image-icon-weather{
    position: absolute;
    width: 26%;
    top:50px;
}
.card-ground{
    width: 100%;
    height: 100%;
    background: #fff;
    box-shadow: 4px 0px 20px rgba(0, 0, 0, 0.25);
    border-radius: 30px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    /* padding-top: 30px; */
    padding-left: 30px;
    padding-right: 30px;
}
.information {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
.name {
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: bold;
    font-size: 27px;
    line-height: 24px;
    color: #332821;
    display: flex;
    justify-content: flex-start;
}
.option-temp {
    display: flex;
    flex-direction: row;
}
.temp {
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: bold;
    font-size: 95px;
    line-height: 77px;
    color: #332821;
    margin: 0;
}
.temp-icon {
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: 500;
    font-size: 17px;
    line-height: 17px;
    color: #332821;
}
.date {
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: 500;
    font-size: 18px;
    line-height: 21px;
    color: rgba(51, 40, 33, 0.5);
    display: flex;
    justify-content: flex-start;
}
.condition-weather .Clouds {
    background: #6A75BA;
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    color: #fff;
    width: auto;
    padding-left: 5px;
    padding-right: 5px;
    padding-top: 1px;
    padding-bottom: 1px;
    border-radius: 15px;
}
.condition-weather .Clear {
    background: #5d6dff;
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: 500;
    font-size: 14px;
    color: #fff;
    width: auto;
    padding-left: 5px;
    padding-right: 5px;
    padding-top: 1px;
    padding-bottom: 1px;
    border-radius: 15px;
}
.view-stats {
    background: #5E4FC1;
    color: #fff;
    font-family: Alegreya Sans;
    font-style: normal;
    font-weight: bold;
    font-size: 24px;
    border: none;
    padding-left: 40px;
    padding-right: 40px;
    padding-top: 15px;
    padding-bottom: 15px;
    border-radius: 18px;
    position: relative;
    top: -30px;
}
</style>

<script>

// console.log(this.index)

export default {
    props: ['card', 'index', 'cardsLenght'],
    // watch: {
    //     cardsLenght() {
    //         if(this.index === (this.cardsLenght / 2)) {
    //             this.zoomCard()
    //         }
    //     }
    // },
    // () {
    //             // console.log(1)
    //             this.zoomCard()
    // },
    methods: {
        formatDataTime() {
            // console.log(this.card.timezone)
            // this.card.timezone = new Date(this.card.timezone)
            // console.log(this.card.timezone)
            let now = new Date()

            // console.log(now.getTime())
            // console.log(this.card.timezone)
            this.card.fullDate = new Date(now.getTime() + (now.getTimezoneOffset() * 60000) + (this.card.timezone*1000))
            this.card.time = `${this.card.fullDate.getHours()}:${this.card.fullDate.getMinutes()}`
            this.card.dayWeek = this.defineDayOfWeek()
            return `${this.card.dayWeek}, ${this.card.time}`
        },
        defineDayOfWeek() {
            switch(this.card.fullDate.getDay()) {
                case 0: return `Sunday`
                case 1: return `Monday`
                case 2: return `Tuesday`
                case 3: return `Wednesday`
                case 4: return `Thursday`
                case 5: return `Friday`
                case 6: return `Saturday`
                default: return ''
            }
        },
        zoomCard() {
            console.log(this.index)
        }
        // defineImageIconWeather() {
        //     console.log(this.card.weather[0].main)
        //     switch(this.card.weather.main) {
        //         case 'Clouds': return "../image/cloud.png"
        //         case 'Clear': return "ada"
        //     }
        // }
    }
}

</script>
