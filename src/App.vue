<script setup lang="ts">
import { ref } from "vue";

const number = ref("");

function go() {
  console.log(number.value);
}

function handleChange(e: Event) {
  number.value = (e.target as HTMLInputElement).value;
}
</script>

<template>
  <div
    class="h-screen w-screen bg-green-100 flex items-center justify-center flex-col"
  >
    <div class="my-5">This tool helps you to go the whatsapp chat easily.</div>
    <div class="w-[500px] bg-white p-5 rounded">
      <img class="my-5 mx-auto" src="../src/assets/whatsapp.svg" />
      <input
        class="py-5 px-3 border w-full focus-visible:outline-green-900"
        placeholder="Input whatsapp number"
        @change.prevent="handleChange"
      />
      <div class="mt-4">
        <button
          class="bg-green-500 py-3 px-5 text-white w-full rounded"
          @click="go"
        >
          Go
        </button>
      </div>
    </div>
  </div>
</template>
