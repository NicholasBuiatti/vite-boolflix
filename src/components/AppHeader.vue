<script>
// import FILE from 'PERCORSO';
import axios from 'axios';
import store from '../data/store.js';
export default {
    name: "",
    components: {

    },
    props: {
    },
    data() {
        return {
            store,
            searchInput: 'Batman',
        }
    },
    methods: {
        // changeLngInFlag() {
        //     for (let i = 0; i < store.moviesList.length; i++) {
        //         const element = store.moviesList[i];
        //         console.log(element);
        //         // if (element.original_language == 'en') {
        //         //     element.original_language = './flagIcon/en.svg'
        //         // }

        //     }
        // },
        searchMovies() {
            //RICHIAMO DAL SERVER LA LISTA DEI FILM CON TUTTE LE SPECIFICHE AL CLICK SUL BUTTON
            const options = {

                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/movie',
                //L'INPUT UNTENTE PRESO DALLO STORE VIENE INSERITO NEL QUERY
                params: { query: this.searchInput, include_adult: 'false', language: 'it-IT', page: '1' },
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
                    for (let i = 0; i < store.moviesList.length; i++) {
                        const element = store.moviesList[i];
                        console.log(element);
                        if (element.original_language == 'en') {
                            element.flag = 'en.svg';
                        } else if (element.original_language == 'it') {
                            element.flag = 'it.svg';
                        } else if (element.original_language == 'es') {
                            element.flag = 'es.svg';
                        } else if (element.original_language == 'gr') {
                            element.flag = 'gr.svg';
                        } else {
                            element.flag = 'No flag'
                        }

                    }
                    console.log(store.moviesList);
                })
                .catch(function (error) {
                    console.error(error);
                });
        },

        searchSeries() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/tv',
                params: { query: this.searchInput, include_adult: 'false', language: 'en-US', page: '1' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkMzZjNjA5NmNiYTM4ZWE1ZWM3OTA1ZDc0YWU5Y2I0YSIsInN1YiI6IjY2NTcyN2M5MTIzMjQ1ODQwOTU5OTc3NiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mF9LoLQkeAs3GL34C9GmZhrrCks7Hf_0Ip3qvACB9YY'
                }
            };

            axios
                .request(options)
                .then(function (response) {
                    //SALVO L'ARRAY DI RISPOSTA NELLA VARIABILE GLOBALE CHE è NELLO STORE.JS
                    store.seriesList = response.data.results;
                    console.log(store.seriesList);
                })
                .catch(function (error) {
                    console.error(error);
                });
        }
    },
    created() {

    },
    mounted() {

    }
}
</script>

<template>
    <section class="container-fluid position-fixed bg-dark">
        <div class="row justify-content-between align-items-center">
            <h1 class="col-3 text-danger">BOOLFLIX</h1>
            <div class="col-5">
                <!-- @keyup="searchMovies()" -->
                <input v-model="searchInput" class="col-9" type="text">
                <button @click="searchMovies(), searchSeries()" class="col-2 ms-2">Search</button>
            </div>
            <!-- <div class="col-2 text-end">
                <a class="ms-2" href="#">icon</a>
                <a href="#">icon</a>
                <a href="#">icon</a>
            </div> -->

        </div>
    </section>
</template>

<style scoped>
section {
    height: 5rem;
}
</style>