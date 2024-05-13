<script setup>
import { ref } from 'vue';
import Todos from './components/Todos.vue';
import Post from './components/Post.vue';


const selectedMenu = ref('');

const handleMenuClick = (menu) => {
  selectedMenu.value = menu;
};
</script>

<template>
  <div>
    <button @click="handleMenuClick('Todos')">Todos</button>
    <button @click="handleMenuClick('Post')">Post</button>

    <div>
      <!-- Menampilkan komponen Todos jika menu Todos dipilih -->
      <Todos v-if="selectedMenu === 'Todos'" />

      <!-- Menampilkan komponen Post jika menu Post dipilih -->
      <Post v-if="selectedMenu === 'Post'" />

      <!-- Pesan ketika tidak ada menu yang dipilih -->
      <p v-if="!selectedMenu">No menu selected</p>
    </div>
  </div>
</template>