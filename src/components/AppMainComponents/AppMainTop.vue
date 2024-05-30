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
            lastImg: 6,
            firstImg: 0,
        }
    },
    methods: {
        classDNone(index) {
            if (index >= this.firstImg && index < this.lastImg) {
                return ''
            } else {
                return 'd-none'
            }
        },
        next(arryaList) {
            this.lastImg++;
            this.firstImg++;
            if (this.lastImg == arryaList.length + 1) {
                this.firstImg = (arryaList.length - 6)
                this.lastImg = arryaList.length
            }
        },
        back(arryaList) {
            this.lastImg--;
            this.firstImg--;
            console.log(arryaList.length);
            if (this.firstImg == -1) {
                this.firstImg = 0
                this.lastImg = 6
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
    <h4 class="text-white">Sono stati trovati {{ this.store.moviesList.length }} film</h4>

    <!-- CREO UN CONTAINER BOX CON OVERFLOW PER CONTENERE I MIEI POSTER SU UN UNICA RIGA -->
    <div class="row flex-nowrap w-100 justify-content-between">
        <div v-for="movie, i in this.store.moviesList" :class="classDNone(i)" class="col-3 position-relative"
            id="containerPoster">
            <!-- <template v-if="i < 5"> -->
            <img :src="`https://image.tmdb.org/t/p/w342/${movie.poster_path}`" alt="" id="poster">

            <div class="text-white p-2 position-absolute" id="infoMovie">
                <h6>Titolo originale: {{ movie.original_title }}</h6>
                <h6>Titolo tradotto: {{ movie.title }}</h6>
                <h6>Lingua originale: {{ movie.original_language }}</h6>
                <img :src="getImg(movie.flag)" :class="movie.flag == 'No flag' ? 'd-none' : ''" alt="" id="flag">
                <!-- APPROSIMAZIONE DEL VOTO AL LIMITE PIù VICINO DIVIDENDOLO PER 2 -->
                <h6>Voto: {{ Math.round(movie.vote_average / 2) }}</h6>
                <!-- METTO TANTE STELLE QUANTO è IL VOTO E NON MI PIACE CHE UN 3.4 DIVENTI UN 4 -->
                <span v-for="star in Math.round(movie.vote_average / 2)">★</span>
                <span v-for="noStar in (5 - (Math.round(movie.vote_average / 2)))">☆</span>
                <h6>{{ movie.release_date }}</h6>
            </div>
            <!-- </template> -->
        </div>

    </div>
    <button @click="next(this.store.moviesList)">avanti</button>
    <button @click="back(this.store.moviesList)">indietro</button>
    <!-- <pre class="bg-primary">{{ this.store.moviesList }}</pre> -->
</template>

<style scoped>
#flag {
    width: 5rem;
    height: 3rem;
}

#containerPoster {
    width: 15rem;
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