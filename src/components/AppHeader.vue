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
            searchInput: '',
            URLMovies: 'https://api.themoviedb.org/3/search/movie',
            URLSeries: 'https://api.themoviedb.org/3/search/tv',

        }
    },
    methods: {
        searchMovies() {
            this.visibleMovies = false;
            this.store.moviesListBase = []
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
                    store.moviesList = response.data.results;
                })
                .catch(function (error) {
                    console.error(error);
                });
        },
        searchSeries() {
            const options = {
                method: 'GET',
                url: 'https://api.themoviedb.org/3/search/tv',
                params: { query: this.searchInput, include_adult: 'false', language: 'it-IT', page: '1' },
                headers: {
                    accept: 'application/json',
                    Authorization: 'Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJkMzZjNjA5NmNiYTM4ZWE1ZWM3OTA1ZDc0YWU5Y2I0YSIsInN1YiI6IjY2NTcyN2M5MTIzMjQ1ODQwOTU5OTc3NiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.mF9LoLQkeAs3GL34C9GmZhrrCks7Hf_0Ip3qvACB9YY'
                }
            };
            axios
                .request(options)
                .then(function (response) {
                    store.seriesList = response.data.results;
                })
                .catch(function (error) {
                    console.error(error);
                });
        },
    },
    created() {

    },
    mounted() {

    }
}
</script>

<template>
    <section class="container-fluid bg-dark">
        <div class="row justify-content-between align-items-center">
            <h1 class="col-3 text-danger">BOOLFLIX</h1>
            <div class="col-5 text-end row m-0">
                <input v-model="searchInput" class="w-75 form-control me-2 border-danger" type="search"
                    placeholder="Search" aria-label="Search" id="searchBar">
                <button @click="searchMovies(), searchSeries()"
                    class="col-2 btn btn-outline-danger ms-2">Search</button>
            </div>
        </div>
    </section>
</template>

<style scoped>
section>div {
    height: 4rem;
}

#searchBar:focus {
    box-shadow: 0 0 0 .25rem rgba(252, 0, 0, 0.604)
}
</style>