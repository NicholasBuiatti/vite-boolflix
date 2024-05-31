<script>
// import FILE from 'PERCORSO';
import axios from 'axios';
import store from './data/store.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue'
export default {
    name: "",
    components: {
        AppHeader,
        AppMain,
    },
    props: {
    },
    data() {
        return {
            store,
        }
    },
    methods: {

    },
    mounted() {
        //RICHIAMO DAL SERVER LA LISTA DEI FILM CON TUTTE LE SPECIFICHE AL CLICK SUL BUTTON
        const options = {
            method: 'GET',
            url: 'https://api.themoviedb.org/3/trending/movie/day?language=it-IT', headers: {
                accept: 'application/json',
                Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkMzZjNjA5NmNiYTM4ZWE1ZWM3OTA1ZDc0YWU5Y2I0YSIsInN1YiI6IjY2NTcyN2M5MTIzMjQ1ODQwOTU5OTc3NiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mF9LoLQkeAs3GL34C9GmZhrrCks7Hf_0Ip3qvACB9YY'
            }
        };
        axios
            .request(options)
            .then(function (response) {
                //SALVO L'ARRAY DI RISPOSTA NELLA VARIABILE GLOBALE CHE è NELLO STORE.JS
                store.moviesListBase = response.data.results;
            })
            .catch(function (error) {
                console.error(error);
            });
        const options1 = {
            method: 'GET',
            url: 'https://api.themoviedb.org/3/tv/top_rated?language=it_IT&page=1', headers: {
                accept: 'application/json',
                Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkMzZjNjA5NmNiYTM4ZWE1ZWM3OTA1ZDc0YWU5Y2I0YSIsInN1YiI6IjY2NTcyN2M5MTIzMjQ1ODQwOTU5OTc3NiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mF9LoLQkeAs3GL34C9GmZhrrCks7Hf_0Ip3qvACB9YY'
            }
        };
        axios
            .request(options1)
            .then(function (response) {
                //SALVO L'ARRAY DI RISPOSTA NELLA VARIABILE GLOBALE CHE è NELLO STORE.JS
                store.seriesListBase = response.data.results;
                console.log(store.seriesListBase);
            })
            .catch(function (error) {
                console.error(error);
            });
    }
}
</script>

<template>
    <AppHeader />
    <AppMain />
</template>

<style scoped></style>
