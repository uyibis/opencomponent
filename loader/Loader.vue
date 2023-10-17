<template>
    <div class="text-center">
        <div v-if="loading" class="spinner-border text-primary" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>
</template>

<script>
export default {
    name: "Loader",
    props:['loading']
    ,
    // data() {
    //     return {
    //         loading: false,
    //     };
    // },
    // methods: {
    //     // Call this method to show the loader
    //     showLoader() {
    //         this.loading = true;
    //     },
    //     // Call this method to hide the loader
    //     hideLoader() {
    //         this.loading = false;
    //     },
    // },
}
</script>

<style scoped>

</style>
