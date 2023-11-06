# `Loader` Vue Component

The `Loader` component is a Vue component that provides a loading indicator, typically displayed while content is being loaded or processed.

## Usage

To use the `Loader` component, you can import it and include it in your Vue application. Here's an example of how to use it:

```vue
<template>
  <div>
    <loader :loading="isLoading" />
  </div>
</template>

<script>
import Loader from "@/components/Loader.vue";

export default {
  components: {
    Loader,
  },
  data() {
    return {
      isLoading: true, // Set this to `true` to display the loader
    };
  },
  methods: {
    // Your logic to toggle `isLoading`
  },
};
</script>
