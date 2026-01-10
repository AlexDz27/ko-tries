<script setup>
import { computed, watch } from 'vue'

const { number } = defineProps({
  number: {
    type: Number,
  }
})
const emit = defineEmits(['onTwelve'])

watch(() => number, async (oldVal, newVal) => {
  if (oldVal === 12) {
    emit('onTwelve')
    alert('got 12')
  }
})

const fontSize = computed(() => Math.max(number, 10))
</script>

<template>
  <p>
    <b :style="{fontSize: `${fontSize}px`}">{{ number }}</b>
  </p>
</template>
