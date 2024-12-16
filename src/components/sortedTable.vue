<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th></th>
                    <th>Title</th>
                    <th>Genre</th>
                    <th>Time</th>
                    <th>BPM</th>
                    <th>Year</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="s in filtered" :key="s._id">
                    <td>{{ counter++ }}</td>
                    <td>{{ s.TITLE }}</td>
                    <td>{{ s.GENRE }}</td>
                    <td>{{ s.TIME }}</td>
                    <td>{{ s.BPM }}</td>
                    <td>{{ s.YEAR }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
import songsData from '@/songs';
import { computed, defineProps } from 'vue';

const prop = defineProps(['artistId']);
let counter = 1;

const filtered = computed(() => {
    counter = 1;
    const filtered = songsData.filter(song => song.ARTIST_ID == prop.artistId);
    return filtered;
});
</script>

<style scoped>
.table {
    width: 100%;
    margin-bottom: 1rem;
    color: #212529;
    border-collapse: collapse;
    border-spacing: 0;
    border: 1px solid #dee2e6;
}
th{
    background-color: #f8f9fa;
    color: #212529;
    border: 1px solid #dee2e6;
    padding: 0.75rem;
    vertical-align: top;
}
td{
    border: 1px solid #dee2e6;
    padding: 0.75rem;
    vertical-align: top;
}

</style>