<template>
    <div class="audio">
        <audio controls :src="src"></audio>
<!--        <date :date="'08/02/2024'" :time="'10:40'"/>-->
    </div>
</template>

<script>
import date from "./date.vue";

export default {
    components: {
        date,
    },
    props: {
        src: ''
    }
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
