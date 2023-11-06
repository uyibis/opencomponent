# `FileUploader` Vue Component

The `FileUploader` component is a Vue component that provides a user-friendly file upload interface, allowing users to either drag and drop files or browse for files to upload. It also includes a progress bar to track the upload progress.

## Usage

To use the `FileUploader` component, you can import it and include it in your Vue application. Here's an example of how to use it:

```vue
<template>
  <div>
    <file-uploader :url="uploadUrl" @file-uploaded="handleFileUploaded" />
  </div>
</template>

<script>
import FileUploader from "@/components/FileUploader.vue";

export default {
  components: {
    FileUploader,
  },
  data() {
    return {
      uploadUrl: "/your-upload-endpoint",
    };
  },
  methods: {
    handleFileUploaded(fileInfo) {
      // Handle the uploaded file information
      console.log("File uploaded:", fileInfo);
    },
  },
};
</script>
