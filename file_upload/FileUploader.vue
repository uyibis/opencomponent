<template>
    <div class="dashed_upload">
        <div class="wrapper">
        <div class="drop">
            <div class="cont">
                <i class="fa fa-cloud-upload"></i>
                <div class="tit">
                    Drag & Drop
                </div>
                <div class="desc">
                    or
                </div>
                <div class="browse bg-light text-primary">
                    click here to browse
                </div>
            </div>
            <input id="files"   @change="uploadFile" type="file" />
            <ProgressBar :progress="uploadProgress" />
        </div>
    </div>
    </div>
<!--    <div>-->

<!--        <label for="upl" >Upload Media</label>-->
<!--        <input id="upl" type="file" @change="uploadFile" hidden/>-->
<!--        <ProgressBar :progress="uploadProgress" />-->
<!--    </div>-->
</template>

<script>
import ProgressBar  from "../progress/Progress.vue";
import axios from 'axios';
export default {
    name: "FileUploader",
    props:['url'],
    components: {
        ProgressBar,
    },
    data() {
        return {
            uploadProgress: 0,
        };
    },
    methods: {
        uploadFile(event) {
            const file = event.target.files[0];
            this.uploadProgress=0;
            const formData = new FormData();
            formData.append('file', file);

            // Simulate an upload progress (you can replace this with your actual upload logic)
            axios.post(this.url, formData, {
                    onUploadProgress: (progressEvent) => {
                        this.uploadProgress = Math.round((progressEvent.loaded / progressEvent.total) * 100);
                    },
                })
                .then((response) => {
                    // Handle successful upload response from the server
                    let res=response.data;
                    this.$emit('file-uploaded', res);
                    //console.log('File uploaded successfully:', response.data);
                })
                .catch((error) => {
                    // Handle upload errors
                    this.uploadProgress=0;
                    console.error('Error uploading file:', error);
                });
        },
    },
    mounted() {
        console.log('url',this.url);
    }

}
</script>

<style scoped>
*, *:before, *:after {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}

input:focus, select:focus, textarea:focus, button:focus {
    outline: none;
}

.drop {
    width: 90%;
    max-width: 500px; /* Added max-width for responsiveness */
    height: 220px;
    border: 3px dashed #DADFE3;
    border-radius: 15px;
    overflow: hidden;
    text-align: center;
    background: transparent;
    -webkit-transition: all 0.5s ease-out;
    -moz-transition: all 0.5s ease-out;
    transition: all 0.5s ease-out;
    margin: 0 auto 10px; /* Simplified margin */
    position: relative; /* Changed from absolute to relative */
}

.drop .cont {
    width: 100%; /* Adjusted width for responsiveness */
    height: 170px;
    color: #8E99A5;
    -webkit-transition: all 0.5s ease-out;
    -moz-transition: all 0.5s ease-out;
    transition: all 0.5s ease-out;
    margin: auto;
    position: relative; /* Changed from absolute to relative */
}

.drop .cont i {
    font-size: 40px;
    color: #787e85;
    position: relative;
}

.drop .cont .tit {
    font-size: 30px;
    text-transform: uppercase;
    font-weight: 900;
}

.drop .cont .desc {
    color: #787e85;
    font-size: 18px;
}

.drop .cont .browse {
    margin: 10px auto; /* Centered the element horizontally */
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
}

.drop input {
    width: 100%;
    height: 100%;
    cursor: pointer;
    background: red;
    opacity: 0;
    position: absolute;
    top: 0;
    left: 0;
}

#list {
    width: 100%;
    text-align: left;
    position: absolute;
    left: 0;
    top: 0;
}

.dashed_upload {
    height: 230px;
}

/* Media Query for screens with a maximum width of 768px */
@media screen and (max-width: 768px) {
    .drop {
        width: 100%; /* Full width on smaller screens */
    }
}

</style>
