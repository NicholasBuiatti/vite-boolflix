<script>
// import FILE from 'PERCORSO';
import AppMainTop from './AppMainComponents/AppMainTop.vue';
import AppMainMid from './AppMainComponents/AppMainMid.vue';
export default {
    name: "",
    components: {
        AppMainTop,
        AppMainMid,
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
            <div class="col-12 overflow-auto" id="containerfilm">
                <AppMainTop />
                <AppMainMid />
            </div>

        </div>

    </section>
</template>

<style scoped>
section {
    height: calc(100vh - 5rem);
    background: linear-gradient(to bottom, #a90329 0%, #8f0222 47%, #6d0019 100%);
}
</style>