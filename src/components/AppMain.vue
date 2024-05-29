<script>
// import FILE from 'PERCORSO';
import AppMainNavBar from './AppMainComponents/AppMainNavBar.vue';
import AppMainTop from './AppMainComponents/AppMainTop.vue';
import AppMainMid from './AppMainComponents/AppMainMid.vue';
import AppMainBottom from './AppMainComponents/AppMainBottom.vue';
export default {
    name: "",
    components: {
        AppMainNavBar,
        AppMainTop,
        AppMainMid,
        AppMainBottom,
    },
    props: {
    },
    data() {
        return {

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
    <section class="container-fluid">
        <div class="row overflow-auto">
            <!-- <AppMainNavBar class="col-1" /> -->
            <div class="col-12 overflow-auto" id="containerfilm">
                <AppMainTop />
                <AppMainMid />
                <AppMainBottom />
            </div>

        </div>

    </section>
</template>

<style scoped>
section {
    padding-top: 5rem;
    height: 100vh;
    background: linear-gradient(to bottom, #a90329 0%, #8f0222 47%, #6d0019 100%);
}

#containerfilm {
    height: calc(100vh - 5rem);
}
</style>