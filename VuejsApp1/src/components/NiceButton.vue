<script setup>

</script>

<template>
    <button class="fancy-button">
      <slot></slot>
    </button>
</template>

<script>
export default {
  name: 'NiceButton',
  props: {}
}
</script>

<style scoped>

.fancy-button {
  background-color: azure;
  color: black;
}

</style>