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
