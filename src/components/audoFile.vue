<template>
    <div class="audio">
        <audio controls src="https://file-examples.com/storage/fe98e6ab1965df346a899de/2017/11/file_example_MP3_700KB.mp3"></audio>
        <date :date="'08/02/2024'" :time="'10:40'"/>
    </div>
</template>

<script>
import date from "./date.vue";

export default {
    components: {
        date,
    },
}
</script>

<style scoped>
.audio {
    max-width: 100%;
    background-color: #E6E9EF;
    padding: 16px 10px 16px 10px;
    border-radius: 16px;
    margin: 16px 26px;
    position: relative;
}
.audio audio {
    width: 100%;
    height: 30px;
}
</style>
