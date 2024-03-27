<template>
    <div class="button">
        <button class="button-btn ml-20 button-line" @click="openModal">Запланировать звонок</button>
        <button class="button-btn" @click="goTo(6)">Звонок роботом</button>
        <button class="button-btn" @click="goTo(6)">Звонок</button>
        <button class="button-btn" @click="goTo(6)">Товар продан</button>
        <button class="button-btn" @click="goTo(6)">Внести товар</button>
        <button class="button-btn mr-20" @click="goTo(6)">Отбор пробы</button>
    </div>
</template>

<script>
import axios from "axios";

export default {
    props: {
        dealId: Number
    },
    methods: {
        openModal() {
            this.$emit('openModal', true);
        },
        async goTo(idx) {
            const response = await axios.get(`http://172.201.225.48:5004/${this.dealId}?button_id=${idx}`);
            console.log(response);
            if(response) {
                if(response.data.result === 'Success') {
                    console.log('dasdas');
                    window.open(response.data.url, '_blank');
                }
            }
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