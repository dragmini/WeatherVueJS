<template>
    <div class="header">
        <p class="logo">Weather Api</p>
        <div class="search">
            <input v-model="searchText" class="search-city" type="text" placeholder="В каком городе вы хотите посмотреть погоду?">
            <div @click="searchClickHandler"><i class="bi bi-search"></i></div>
        </div>
        <button class="options" @click="optionsClickHandler"><i class="bi bi-gear"></i></button>
    </div>
</template>

<style>
@import '~bootstrap-icons/font/bootstrap-icons.css';

.header{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    padding-left: 20px;
    padding-right: 20px;
    /* margin: 0px; */
}
.logo {
    border-radius: 50%;
    width: 100px;
    height: 100px;
    border: 1px #fff solid;
    color: #fff;
    font-size: 20px;
    display: flex;
    align-items: center;
}
.options {
    background: transparent;
    border: none;
}
.options i {
    color: #fff;
    font-size: 35px;
}
.search-city {
    width: 80%;
    height: 55px;
    border-radius: 10px;
    border: none;
    font-size: 20px;
    padding-left: 15px;
    color: rgba(0, 0, 0, 0.6);
}
.search-city::placeholder {
    color: rgba(0, 0, 0, .3);
}
.search-city:focus {
    outline: none;
}
.search {
    width: 60%;
    display: flex;
    flex-direction: row;
    justify-content: center;
}
.search div {
    background: #fff;
    border-radius: 10px;
    width: 8%;
    margin-left: 3px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.search div i {
    font-size: 25px;
}
</style>

<script>
// import CardsCity from './CardsCity.vue'

export default {
    // props: {
    //     searchText: {type: String}
    // },
    data() {
        return {
            searchText: ''
        }
    },
    methods: {
        searchClickHandler() {
            this.$emit('search-weather', {
                searchText: this.searchText,
                });
            // console.log(this.searchText)
        },
        optionsClickHandler() {
            this.$emit('open-options-modal');
        }
    }
}

</script>