# Vue 3 File Uploader Component

![GitHub](https://img.shields.io/github/license/your-username/your-repository)
![GitHub last commit](https://img.shields.io/github/last-commit/your-username/your-repository)
![GitHub issues](https://img.shields.io/github/issues/your-username/your-repository)

A Vue 3 component that provides a user-friendly file upload feature with real-time progress tracking using the integrated progress bar.

## Installation

To use this File Uploader component in your Vue 3 project, follow these steps:

1. **Install the component:**

   You can install the Vue 3 File Uploader component via npm:

    ```bash
   npm install vue3-file-uploader

1. **Usage :**
```bash
   <template>
  <div>
    <FileUploader @file-uploaded="handleFileUpload" />
  </div>
</template>

<script>
import FileUploader from 'vue3-file-uploader';

export default {
  components: {
    FileUploader,
  },
  methods: {
    handleFileUpload(fileData) {
      // Handle the uploaded file data
      console.log('File uploaded:', fileData);
    },
  },
};
</script>

