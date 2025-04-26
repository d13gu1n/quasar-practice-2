<template>
  <div>{{ testLabel.value }}</div>
  <div>{{ apiTest.value }}</div>
</template>

<script setup>
defineProps({
  testLabel: String,
  apiTest: Object
  })
</script>
