<template>
    <div>
        <div id="dialogModal" class="modal fade" :class="{ 'show': show }" tabindex="-1" role="dialog" style="display: none;">
            <div class="modal-dialog modal-dialog-centered">
                <div class="modal-content" style="background: transparent">
                    <div class="modal-body">
                        <Loader :loading="show"/>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Loader from "../loader/Loader.vue";
export default {
    name: "dialog_loader",
    components: {
        Loader,
    },
    props: {
        show: Boolean, // Prop to control whether to show or hide the dialog
    },
    watch: {
        show(newValue) {
            console.log(newValue);
            if (newValue==true) {
                this.showDialog();
            } else {
                this.hideDialog();
            }
        },
    },
    methods: {
        showDialog() {
            // Show the Bootstrap modal
            $('#dialogModal').modal('show');
        },
        hideDialog() {
            // Hide the Bootstrap modal
            $('#dialogModal').modal('hide');
        },
    },
}
</script>

<style scoped>

</style>
