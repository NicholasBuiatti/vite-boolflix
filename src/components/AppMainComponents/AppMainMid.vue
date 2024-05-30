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

    }
}
</script>

<template>
    <h4 class="text-white">Queste sono le serie Tv</h4>
    <div class="row ms-2">
        <div v-for="serie in this.store.seriesList" class="col-3 bg-warning m-2">
            <img :src="`https://image.tmdb.org/t/p/w342/${serie.backdrop_path}`" alt="">
            <h5>Titolo: {{ serie.name }}</h5>
            <h5>Titolo Originale: {{ serie.original_name }}</h5>
            <h5>Lingua: {{ serie.original_language }}</h5>
            <img :src="getImg(serie.flag)" :class="serie.flag == 'No flag' ? 'd-none' : ''" alt="" id="flag">

            <h5>Voto: {{ serie.vote_average }}</h5>
        </div>
    </div>

    <pre class="bg-primary">{{ this.store.seriesList }}</pre>
</template>

<style scoped>
#flag {
    width: 5rem;
    height: 3rem;
}
</style>