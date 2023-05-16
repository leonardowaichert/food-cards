<script setup>

defineProps({
  imageUri: String,
  width: Number,
  length: Number,
  shadow: Boolean,
  title: String,
  description: String,
  stars: Number,
  ranking: String,
  price: Number,
  lastPrice: Number,
});

</script>

<template>
  <div>Hotel Card</div>
</template>

<style scoped lang="scss"></style>
