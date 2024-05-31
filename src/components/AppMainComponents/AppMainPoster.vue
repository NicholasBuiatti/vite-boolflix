<script>
import store from '../../data/store.js';
export default {
    name: "",
    components: {
    },
    props: ["singlePoster"],
    data() {
        return {
            store,
        }
    },
    methods: {
        getFlag(Lng) {
            if (Lng == 'en') {
                return this.getImg('en.svg')
            } else if (Lng == 'it') {
                return this.getImg('it.svg')
            } else if (Lng == 'gr') {
                return this.getImg('gr.svg')
            } else if (Lng == 'es') {
                return this.getImg('es.svg')
            } else {
                return null
            }
        },
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
    <div>
        <img :src="`https://image.tmdb.org/t/p/w342/${singlePoster.poster_path}`" alt="" id="poster">

        <div class="text-white p-2 position-absolute" id="infoMovie">
            <h6>Titolo originale: {{ singlePoster.original_title }}</h6>
            <h6>Titolo tradotto: {{ singlePoster.title }}</h6>
            <h6>Lingua originale: {{ singlePoster.original_language }}</h6>
            <img :src="getFlag(singlePoster.original_language)" :class="singlePoster.flag == 'No flag' ? 'd-none' : ''"
                alt="" id="flag">
            <!-- APPROSIMAZIONE DEL VOTO AL LIMITE PIù VICINO DIVIDENDOLO PER 2 -->
            <h6>Voto: {{ Math.round(singlePoster.vote_average / 2) }}</h6>
            <!-- METTO TANTE STELLE QUANTO è IL VOTO E NON MI PIACE CHE UN 3.4 DIVENTI UN 4 -->
            <span v-for="star in Math.round(singlePoster.vote_average / 2)">★</span>
            <span v-for="noStar in (5 - (Math.round(singlePoster.vote_average / 2)))">☆</span>
            <h6>{{ singlePoster.release_date }}</h6>
        </div>

    </div>
</template>

<style scoped>
#flag {
    width: 5rem;
    height: 3rem;
}

#poster {
    height: 20rem;
    width: 14rem;
}

#infoMovie {
    background-color: #222;
    height: 20rem;
    width: 14rem;
    border: 1px solid white;
    display: none;
}

#containerPoster:hover>#infoMovie {
    display: unset
}


#containerPoster:hover>#poster {
    display: none;
}
</style>