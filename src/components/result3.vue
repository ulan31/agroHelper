<template>
    <article class="message">
        <div class="message-block">
            <span class="message-title">Доп. рекомендация:</span> <span class="message-text">{{ result }}</span>
        </div>
        <date :date="'01.03.2024'" :time="'10:40'"/>
        <what-sapp-icon v-if="isShowWhatSapp"/>
    </article>
</template>

<script>
import date from "./date.vue";
import whatSappIcon from "./whatSappIcon.vue";
import result2 from "./result2.vue";

export default {
    computed: {
        result2() {
            return result2
        }
    },
    components: {
        date,
        whatSappIcon
    },
    props: {
        result: '',
        isShowWhatSapp: {
            type: Boolean,
            default: true
        }
    },
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