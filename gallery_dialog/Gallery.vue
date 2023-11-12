<template>
    <div>
     <div class="card">
        <div class="card-body">
            <button @click="openModal(0)" class="btn btn-outline-primary"><i class="fa fa-plus"/>&nbsp;Media</button>
        </div>
    </div>
        <div class="modal fade" id="galleryModal" tabindex="-1" aria-labelledby="galleryModalLabel" aria-hidden="true">
            <div class="modal-dialog modal-lg">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="galleryModalLabel"><li class="fa fa-camera"/> Select Media</h5> &nbsp; &nbsp;
                        <!-- Button to Remove Media -->
                        <button @click="removeSelectedImages" class="btn btn-link text-primary"><i class="fa fa-times"></i>Remove</button>
                        &nbsp; &nbsp;
                        <button @click="emitSelectedImages" class="btn btn-link text-danger">
                            <i class="fa fa-check"/>
                            Apply</button>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <FileUploader @file-uploaded="addImage" :url="uploader_url" />
                        <!-- Button to Emit Selected Images -->
                        <div class="image-list">
                            <div
                                v-for="(image, index) in images"
                                :key="index"
                                class="image-item"
                                @click="toggleImageSelection(index)"
                                :class="{ selected: image.selected }"
                            >
                                <img v-if="isImageFileType(image)" class="img-thumbnail" :src="image.url" :alt="image.name" />
                                <div v-else >
                                    <video class="video-thumbnail" :src="image.url" controls></video>
                                    <br/>
                                    <label><i class="fa fa-plus"/> select</label>
                                </div>
                                <!-- Use the Loader component when uploading -->
                            </div>
<!--                            <Loader v-if="image.uploading" />-->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import FileUploader from "../file_upload/FileUploader.vue";
import Loader from "../loader/Loader.vue";
export default {
    name: "Gallery",
    props:['uploader_url','gallery_url']
    ,
    components: {
        FileUploader,
        Loader, // Include the Loader component
    },
    data() {
        return {
            images: [],
        };
    },
    methods: {
        addImage(imageData) {
           // console.log('emit hello');
            this.images.push({
                url: imageData.url,
                uploading: false, // Track upload state
                selected: false,
                type:imageData.type,
                id:imageData.id
            });
        },
        toggleImageSelection(index) {
            this.images[index].selected = !this.images[index].selected;
        },

        fetchImagesFromBackend() {
            // Make an HTTP GET request to fetch images from the server
            axios
                .post(this.gallery_url,{})
                .then((response) => {
                    console.log(response);
                    this.images = response.data.map((image) => ({
                        url: image.url,
                        uploading: false, // Set progress to 100 since these are pre-fetched images
                        selected: false,
                        type:image.type,
                        id:image.id
                    }));
                })
                .catch((error) => {
                    console.error('Error fetching images:', error);
                });
        },
        openModal(index) {
            this.selectedImage = this.images[index];
            $('#galleryModal').modal('show'); // Open the Bootstrap modal
        },
        closeModal() {
            //this.selectedImage = this.images[index];
            $('#galleryModal').modal('hide'); // Open the Bootstrap modal
        },
        emitSelectedImages() {
            // Emit selected images to the parent component
            console.log('hello');
            const selectedImages = this.images.filter((image) => image.selected);
            console.log(selectedImages);
            this.$emit("selected_images", selectedImages);
            this.closeModal()

        },
        removeSelectedImages() {
            // Remove selected images from the gallery
            this.images = this.images.filter((image) => !image.selected);
        },
        isImageFileType(file) {
            if (file.type && file.type.includes('image')) {
                return true;
            }
            return false;
        }
    },
    mounted() {
        this.fetchImagesFromBackend()
    }
}
</script>

<style scoped>
.image-list {
    display: flex;
    flex-wrap: wrap;
}

.image-item {
    margin: 10px;
    cursor: pointer;

}

.selected {
    border: 2px solid #007BFF;
}
img{
    height: 10em;
}
.video-thumbnail {
    max-width: 100%;
    height: 10em;
    z-index: -1;

}

</style>
