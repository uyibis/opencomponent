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
    props:['loading'],
}
</script>

<style scoped>

</style>
