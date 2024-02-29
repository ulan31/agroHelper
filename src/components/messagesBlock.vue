<template>
    <article class="message">
        <div class="message-block">
            <span class="message-title">Date:</span> <span class="message-text">08/02/2024</span>
        </div>
        <div class="message-block">
            <span class="message-title">Deal_ID:</span> <span class="message-text">12345678</span>
        </div>
        <div class="message-block">
            <span class="message-title">Call_ID:</span> <span class="message-text">12345678</span>
        </div>
        <div class="message-block">
            <span class="message-title">Farmer_ID:</span> <span class="message-text">12345678 (Иван Иванов)</span>
        </div>
        <div class="message-block">
            <span class="message-title">Crop_ID:</span> <span class="message-text">123 (Подсолнечник)</span>
        </div>
        <div class="message-block">
            <span class="message-title">Storage_ID:</span> <span class="message-text">123</span>
        </div>
        <date :date="'08/02/2024'" :time="'10:40'"/>
        <what-sapp-icon/>
    </article>
</template>

<script>
import date from "./date.vue";
import whatSappIcon from "./whatSappIcon.vue";
export default {
    components: {
        date,
        whatSappIcon
    }
}
</script>

<style scoped>
.message {
    max-width: 100%;
    background-color: #E6E9EF;
    padding: 16px 10px 16px 10px;
    border-radius: 16px;
    margin: 16px 26px;
    position: relative;
}
.message-block {
    display: flex;
    align-items: center;
    gap: 5px;
}
.message-title {
    font-weight: 500;
    font-size: 14px;
    color: #000;
}
.message-text {
    font-size: 14px;
    color: #000;
}
</style>