<script setup lang="ts">
import { ref } from "vue";

const number = ref("");

function go() {
  if (number.value[0] === "0") {
    number.value = number.value.slice(1);
  }

  window.location.replace(`https://wa.me/62${number.value}`);
}

function handleChange(e: KeyboardEvent) {
  if (
    (e.keyCode >= 48 && e.keyCode <= 57) ||
    (e.keyCode >= 96 && e.keyCode <= 105) ||
    e.keyCode === 8
  ) {
    // 0-9 only
    number.value = (e.target as HTMLInputElement).value;
  } else {
    e.preventDefault();
  }
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
        @keydown="handleChange"
        v-model="number"
      />
      <span class="text-xs text-gray-500"
        >Without zero number in the beginning</span
      >
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
