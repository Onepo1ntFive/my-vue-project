<template>
  <button :class="mode">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      required: false,
    },
  },
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #F38181;
  border: 1px solid #F38181;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #FCE38A;
  border-color: #FCE38A;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #F38181;
}
</style>