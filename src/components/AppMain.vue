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
        <div class="row">
            <AppMainNavBar class="col-1" />
            <div class="col-11">
                <AppMainTop />
                <AppMainMid />
                <AppMainBottom />
            </div>

        </div>

    </section>
</template>

<style scoped></style>