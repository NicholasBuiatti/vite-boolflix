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
        //RICHIAMO DAL SERVER LA LISTA DEI FILM CON TUTTE LE SPECIFICHE
        getMovies() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/discover/movie',
                params: {
                    include_adult: 'false',
                    include_video: 'false',
                    language: 'en-US',
                    page: '1',
                    sort_by: 'popularity.desc'
                },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkMzZjNjA5NmNiYTM4ZWE1ZWM3OTA1ZDc0YWU5Y2I0YSIsInN1YiI6IjY2NTcyN2M5MTIzMjQ1ODQwOTU5OTc3NiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mF9LoLQkeAs3GL34C9GmZhrrCks7Hf_0Ip3qvACB9YY'
                }
            };

            axios
                .request(options)
                .then(function (response) {
                    //SALVO L'ARRAY DI RISPOSTA NELLA VARIABILE GLOBALE CHE è NELLO STORE.JS
                    store.moviesList = response.data.results;
                    console.log(store.moviesList);
                })
                .catch(function (error) {
                    console.error(error);
                });
        }
    },
    mounted() {
        //RICHIAMO LA FUNZIONE PER GENERARE L'ARRAY MOVIESLIST NELLO STORE AL MOUNTED
        this.getMovies();

        /* CHIAMATA AXIOS
                axios.get("").then(risultato => {
                    console.log(risultato);
              });*/
    }
}
</script>

<template>
    <AppHeader />
    <AppMain />
</template>

<style scoped></style>
