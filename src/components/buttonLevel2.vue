<template>
    <div class="button">
        <button class="button-btn" @click="goTo">Встречное предложение</button>
        <button class="button-btn" @click="goTo">Анализ</button>
    </div>
</template>

<script>
export default {
    methods: {
        goTo() {
            window.open('https://www.google.ru/?hl=ru', '_blank');
        }
    }
}
</script>

<style scoped>
.button {
    display: flex;
    gap: 16px;
    justify-content: center;
}
.button-btn {
    background-color: #E6E9EF;
    color: #323338;
    font-size: 16px;
    cursor: pointer;
    outline: none;
    padding: 8px 20px;
    border-radius: 8px;
    border: 1px solid #C5C7D0;
    font-weight: 600;
}
.button-btn:hover {
    background-color: #323338;
    color: #fff;
}
</style>