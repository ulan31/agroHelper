<template>
    <div class="date">
        <span class="day">{{ date }}</span>
        <span class="time">{{ time }}</span>
    </div>
</template>

<script>
export default {
    props: {
        date: String,
        time: String
    }
}
</script>

<style scoped>
    .date {
        display: flex;
        color: #676879;
        font-size: 12px;
        gap: 10px;
        position: absolute;
        right: 20px;
        bottom: 10px;
    }
</style>