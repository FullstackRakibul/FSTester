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
  <a-card title="Default size card" style="width: 500px">
    <div class="flex flex-col items-center justify-cente">
      <h2 class="text-2xl font-bold text-blue-600 mb-4">{{ textvalue }}</h2>
      <!-- <input class="border border-gray-300 rounded p-2" v-model="textvalue" @keyup.enter="submitTextValue"
      placeholder="Type and press Enter" /> -->

      <a-textarea v-model:value="textvalue" @keyup.enter="submitTextValue"
        placeholder="Autosize height based on content lines" auto-size />

    </div>
  </a-card>

</template>