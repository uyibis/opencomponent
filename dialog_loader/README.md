# `dialog_loader` Vue Component

The `dialog_loader` component is a Vue component that provides a modal dialog with an embedded loader. It is designed to be a convenient way to display loading indicators within a modal dialog.

## Usage

To use the `dialog_loader` component, you can import it and include it in your Vue application. Here's an example of how to use it:

```vue
<template>
  <div>
    <dialog_loader :show="isLoading" />
  </div>
</template>

<script>
import dialog_loader from "@/components/dialog_loader.vue";

export default {
  components: {
    dialog_loader,
  },
  data() {
    return {
      isLoading: false,
    };
  },
  methods: {
    // Your logic to toggle isLoading
  },
};
</script>
