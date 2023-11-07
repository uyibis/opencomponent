# `Gallery` Vue Component

The `Gallery` component is a Vue component that provides a user-friendly interface for selecting media, including images and videos. Users can upload media, view a gallery of media items, select multiple media items, and apply their selection.

## Usage

To use the `Gallery` component, you can import it and include it in your Vue application. Here's an example of how to use it:

```vue
<template>
  <div>
    <gallery
      :uploader_url="uploaderUrl"
      :gallery_url="galleryUrl"
      @media-selected="handleMediaSelection"
    />
  </div>
</template>

<script>
import Gallery from "@/components/Gallery.vue";

export default {
  components: {
    Gallery,
  },
  data() {
    return {
      uploaderUrl: "/your-uploader-endpoint",
      galleryUrl: "/your-gallery-endpoint",
    };
  },
  methods: {
    handleMediaSelection(selectedMedia) {
      // Handle the selected media items
      console.log("Selected media:", selectedMedia);
    },
  },
};
</script>
```

**Laravel Backend Functions**:

Here are the three Laravel backend functions that can be used with the Gallery component.
```php
public function getUpload(Request $request)
{
    $user = auth()->user(); // Get the authenticated user
    $images = UserUpload::where('user_id', $user->id)->get();

    return $images->map(function ($image) {
        return [
            'id' => $image->id,
            'name' => $image->file_name,
            'url' => asset($image->file_path), // Assumes a public storage setup
            'type' => $image->file_type,
        ];
    });
}
```
