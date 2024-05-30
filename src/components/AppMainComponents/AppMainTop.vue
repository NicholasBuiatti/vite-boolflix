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
        //FUNZIONE PER ESTRAPOLARE IL PERCORSO IMMAGINE
        getImg(flagIcon) {
            let risultato = new URL(`../flagIcon/${flagIcon}`, import.meta.url);
            return risultato.href;
        },
    },
    created() {

    },
    mounted() {
        for (let i = 0; i < array.length; i++) {
            const element = array[i];

        }
    }
}
</script>

<template>
    <h4 class="text-white">Sono stati trovati {{ this.store.moviesList.length }} film</h4>
    <div class="row">
        <div v-for="movie in this.store.moviesList" class="col-3 bg-warning m-2">
            <!-- <pre>{{ movie }}</pre> -->
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.backdrop_path}`" alt="">
            <h5>Titolo: {{ movie.title }}</h5>
            <h5>Titolo Originale: {{ movie.original_title }}</h5>
            <h5>Lingua: {{ movie.original_language }}</h5>
            <img :src="getImg(movie.flag)" :class="movie.flag == 'No flag' ? 'd-none' : ''" alt="" id="flag">
            // APPROSIMAZIONE DEL VOTO AL LIMITE PIù VICINO DIVIDENDOLO PER 2
            <h5>Voto: {{ Math.round(movie.vote_average / 2) }}</h5>
            // METTO TANTE STELLE QUANTO è IL VOTO
            <span v-for="star in Math.round(movie.vote_average / 2)">★</span>
            <span v-for="noStar in (5 - (Math.round(movie.vote_average / 2)))">☆</span>
        </div>
    </div>

    <pre class="bg-primary">{{ this.store.moviesList }}</pre>
</template>

<style scoped>
#flag {
    width: 5rem;
    height: 3rem;
}
</style>