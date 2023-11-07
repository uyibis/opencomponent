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
```

**Database Migration Snippet**:

To use the this component, you may need to create a migration for the `user_uploads` table as follows:

```php
Schema::create('user_uploads', function (Blueprint $table) {
    $table->id();
    $table->foreignId('user_id'); // Assuming you want to associate uploads with users
    $table->string('file_name');
    $table->string('file_path');
    $table->string('file_type');
    $table->integer('file_size');
    $table->string('alt')->nullable(); // Customization
    $table->timestamps();
});
```


**Laravel Backend Functions**:

Here are the three Laravel backend functions that can be used with the File Uploader component.

**Note: We encourage use of cdn.**

1. `upload(Request $request)`: Uploads a file to the server.
   
   ```php
   public function upload(Request $request)
   {
       $request->validate([
           'file' => 'required|mimetypes:image/jpeg,image/png,image/jpg,image/gif,video/mp4,video/quicktime,video/x-msvideo,video/x-flv,video/x-ms-wmv|max:20480000', // Adjust the allowed file types and maximum size as needed
       ]);

       if ($request->hasFile('file')) {
           $file = $request->file('file');

           return $this->UploadHandler($file);
       }

       return response()->json([
           'error' => 'No file uploaded or invalid file type',
       ], 400);
   }
```

    ```php
    private function UploadHandler($image)
    {
    $user = auth()->user(); // Get the authenticated user
    
        if ($user && $image) {
            // Generate a unique file name
            $image_new_name = time() . '_' . $image->getClientOriginalName();
            $image_url = 'images/listing/' . $image_new_name;
    
            $userUpload = new UserUpload([
                'user_id' => $user->id,
                'file_name' => $image_new_name,
                'file_path' => asset($image_url),
                'file_type' => $image->getClientMimeType(),
                'file_size' => $image->getSize(),
            ]);
    
            $isSuccess = $image->move(public_path('images/listing'), $image_new_name);
    
            if ($isSuccess) {
                $userUpload->save();
    
                return [
                    'id' => $userUpload->id,
                    'name' => $userUpload->file_name,
                    'url' => $userUpload->file_path, // Assumes a public storage setup
                    'type' => $userUpload->file_type,
                ];
            }
        }
    
        return false;
    }
```


