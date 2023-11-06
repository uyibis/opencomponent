# `presenter_table_content` Vue Component

The `presenter_table_content` component is a Vue component that allows you to display and navigate through a collection of slides, including images and videos. You can also toggle full-screen mode for images.

## Usage

To use the `presenter_table_content` component, you can import it and include it in your Vue application. Here's an example of how to use it:

```vue
<template>
  <div>
    <presenter_table_content :procedures="procedures" />
  </div>
</template>

<script>
import presenter_table_content from "@/components/presenter_table_content.vue";

export default {
  components: {
    presenter_table_content,
  },
  data() {
    return {
      procedures: [] // Replace with your data
    };
  },
};
</script>
