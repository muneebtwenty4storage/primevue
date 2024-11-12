<template>
  <div class="about">
    <div class="card flex flex-col items-center gap-6">
      <FileUpload mode="basic" @select="onFileSelect" customUpload auto class="p-button-info p-button-outlined"
        icon="pi pi-user" />

      <img v-if="src" :src="src" alt="Image" class="shadow-md rounded-xl w-full sm:w-64"
        style="filter: grayscale(100%)" />
    </div>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

<script setup lang="ts">
import Button from "primevue/button";
import FileUpload from 'primevue/fileupload';
import { ref } from "vue";

const src = ref(null);

function onFileSelect(event) {
  const file = event.files[0];
  const reader = new FileReader();

  reader.onload = async (e) => {
    src.value = e.target.result;
  };

  reader.readAsDataURL(file);
}
</script>
