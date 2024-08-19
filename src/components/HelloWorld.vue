<script setup lang="ts">
import { ref } from 'vue'

const textvalue = ref<string>('');

const submitTextValue = (event: Event) => {
  const submitValue = event.target as HTMLInputElement | null
  textvalue.value = submitValue?.value ? submitValue.value : 'Please enter input first.'
  console.log(submitValue?.value ? submitValue.value : 'Please enter input first.');
}

</script>


<template>
  <h2>{{ textvalue }}</h2>
  <input v-model="textvalue" @keyup.enter="submitTextValue" />

</template>