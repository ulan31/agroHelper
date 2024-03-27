<template>
    <article class="message">
        <div class="message-block">
            <span class="message-title">Дата:</span> <span class="message-text">{{ new Intl.DateTimeFormat('ru').format(new Date(message.date_create)) }}</span>
        </div>
        <div class="message-block">
            <span class="message-title">Номер сделки:</span> <span class="message-text">{{ message.deal_id }}</span>
        </div>
        <div class="message-block">
            <span class="message-title">Номер звонка:</span> <span class="message-text">{{ message.id }}</span>
        </div>
        <div class="message-block">
            <span class="message-title">ФИО Фермера:</span> <span class="message-text">{{ message.title }}</span>
        </div>
        <div class="message-block">
            <span class="message-title">Культура:</span> <span class="message-text">{{ message.culture }}</span>
        </div>
        <div class="message-block">
            <span class="message-title">Склад:</span> <span class="message-text">{{ message.location }}</span>
        </div>
        <date :date="'01.03.2024'" :time="'10:40'"/>
        <what-sapp-icon v-if="isShowWhatSapp"/>
    </article>
</template>

<script>
import date from "./date.vue";
import whatSappIcon from "./whatSappIcon.vue";

export default {
    components: {
        date,
        whatSappIcon
    },
    props: {
        message: Array,
        isShowWhatSapp: {
            type: Boolean,
            default: true
        }
    },
    mounted() {
        console.log('dsa', this.message)
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