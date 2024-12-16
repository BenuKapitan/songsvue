<template>
  <div>
      <select name="eloadok" id="eloadok" @change="artistSelected">
        <option value="null"></option>
        <option v-for="a in artistData" :key="a.id" :value="a._id">{{ a.artist }}</option>
      </select>
      <sortedTable v-if="selected != null" :artistId="selected"></sortedTable>
  </div>
  </template>
  
  <script setup>
  import artistData from '@/artists';
  import { ref } from 'vue';
  import sortedTable from './components/sortedTable.vue';

  const selected = ref(null);

  function artistSelected(event) {
    const artistId = event.target.value;
    selected.value = artistId;
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
  select {
    padding: 5px;
    margin: 10px;
  }

  </style>