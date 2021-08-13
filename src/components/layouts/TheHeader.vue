<template>
  <slot>
    <h1>{{ title }}</h1></slot
  >
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: false,
    },
  },
};
</script>