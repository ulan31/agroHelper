<template>
    <div class="button">
        <button class="button-btn ml-20 button-line" @click="openModal">Запланировать звонок</button>
        <button class="button-btn" @click="goTo">Звонок роботом</button>
        <button class="button-btn" @click="goTo">Звонок</button>
        <button class="button-btn" @click="goTo">Товар продан</button>
        <button class="button-btn" @click="goTo">Внести товар</button>
        <button class="button-btn mr-20" @click="goTo">Отбор пробы</button>
    </div>
</template>

<script>
export default {
    methods: {
        openModal() {
            this.$emit('openModal', true);
        },
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
.button-line {
    border: 2px solid #FFDE5F;
}
</style>