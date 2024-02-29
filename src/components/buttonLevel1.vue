<template>
    <div class="button">
        <button class="button-btn ml-20">Запланировать звонок</button>
        <button class="button-btn">Звонок роботом</button>
        <button class="button-btn">Звонок</button>
        <button class="button-btn">Товар продан</button>
        <button class="button-btn">Внести товар</button>
        <button class="button-btn mr-20">Отбор пробы</button>
    </div>
</template>

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
    border: 1px solid #323338;
}
.button-btn:hover {
    background-color: #323338;
    color: #fff;
}
</style>