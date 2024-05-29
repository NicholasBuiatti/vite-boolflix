<script>
// import FILE from 'PERCORSO';
import store from '../../data/store.js';
export default {
    name: "",
    components: {

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
    created() {

    },
    mounted() {

    }
}
</script>

<template>
    <h4 class="text-white">Sono stati trovati {{ this.store.moviesList.length }} film</h4>
    <div class="row">
        <div v-for="movie in this.store.moviesList" class="col-3 bg-warning m-2">
            <h5>Titolo: {{ movie.title }}</h5>
            <h5>Titolo Originale: {{ movie.original_title }}</h5>
            <h5>Lingua: {{ movie.original_language }}</h5>
            <h5>Voto: {{ movie.vote_average }}</h5>
        </div>
    </div>

    <pre class="bg-primary">{{ this.store.moviesList }}</pre>
</template>

<style scoped></style>