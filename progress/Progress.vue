<template>
    <div class="progress">
        <div class="progress-bar" :style="{ width: progress + '%' }" role="progressbar" :aria-valuenow="progress" aria-valuemin="0" aria-valuemax="100">
            {{ progress }}%
        </div>
    </div>
</template>

<script>
export default {
    name: "Progress",
    props: {
        progress: {
            type: Number,
            required: true,
            default: 0,
        },
    },
}
</script>

<style scoped>
.progress-bar {
    transition: width 0.6s;
    height: 2px;
}
.progress{
    height: 2px;
}
</style>
