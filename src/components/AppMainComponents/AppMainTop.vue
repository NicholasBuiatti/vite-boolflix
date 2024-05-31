<script>
// import FILE from 'PERCORSO';
import store from '../../data/store.js';
import AppMainPoster from './AppMainPoster.vue';
export default {
    name: "",
    components: {
        AppMainPoster,
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

    },
    created() {

    },
    mounted() {

    }
}
</script>

<template>
    <h4 class="text-white">Lista Film</h4>
    <!-- CREO UN CONTAINER BOX CON OVERFLOW PER CONTENERE I MIEI POSTER SU UN UNICA RIGA -->
    <div class="row flex-nowrap w-100 justify-content-between">
        <template v-if="this.store.moviesListBase.length !== 0">
            <AppMainPoster v-for="movie, i in this.store.moviesListBase" :class="classDNone(i)" :singlePoster=movie
                class="col-3 position-relative" id="containerPoster" />
        </template>
        <template v-else>
            <AppMainPoster v-for="movie, i in this.store.moviesList" :class="classDNone(i)" :singlePoster=movie
                class="col-3 position-relative" id="containerPoster" />
        </template>

    </div>
    <button @click="back(this.store.moviesList)">indietro</button>
    <button @click="next(this.store.moviesList)">avanti</button>
</template>

<style scoped>
#containerPoster {
    width: 15rem;
}
</style>