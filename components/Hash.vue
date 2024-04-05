<template>
  <input
    v-model="inputValue" placeholder="Enter text to hash..."
    class="w-full p-2 bg-green-900 text-white placeholder-gray-300 border border-green-700 rounded-md focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent"
  >

  <div v-for="(h, algorithm) in hashStrings" :key="algorithm" class="break-words pt-4">
    <h3>
      {{ algorithm }}
    </h3>
    <span>
      {{ h }}
    </span>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue'

type HashAlgorithm = 'SHA-1' | 'SHA-256' | 'SHA-384' | 'SHA-512'
const algorithms: HashAlgorithm[] = ['SHA-256', 'SHA-512', 'SHA-1', 'SHA-384']

async function hash(algorithm: HashAlgorithm, message: string) {
  const msgUint8 = new TextEncoder().encode(message) // encode as (utf-8) Uint8Array
  const hashBuffer = await crypto.subtle.digest(algorithm, msgUint8) // hash the message
  const hashArray = Array.from(new Uint8Array(hashBuffer)) // convert buffer to byte array
  const hashHex = hashArray
    .map(b => b.toString(16).padStart(2, '0'))
    .join('') // convert bytes to hex string
  return hashHex
}

const inputValue = ref('')
const hashStrings = ref<{
  [key in HashAlgorithm]: string
}>({
  'SHA-1': '',
  'SHA-256': '',
  'SHA-384': '',
  'SHA-512': '',
})

watchEffect(() => {
  algorithms.forEach(async (algorithm) => {
    hashStrings.value[algorithm] = await hash(algorithm, inputValue.value)
  })
})
</script>

<style lang="scss" scoped>

</style>
