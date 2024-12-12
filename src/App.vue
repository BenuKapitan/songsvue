<template>
  <div>
      <select name="artists" id="artists" @change="artistSelected">
        <option value="null"></option>
        <option v-for="artist in artistData" :key="artist.id" :value="artist._id">{{ artist.artist }}</option>
      </select>
      <sortedTable v-if="selectedArtist != null" :artistId="selectedArtist"></sortedTable>
  </div>
  </template>
  
  <script setup>
  import artistData from '@/artists';
  import { ref } from 'vue';
  import sortedTable from './components/sortedTable.vue';

  const selectedArtist = ref(null);

  function artistSelected(event) {
    const artistId = event.target.value
    selectedArtist.value = artistId;
  }
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  </style>