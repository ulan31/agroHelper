<template>
    <div class="footer">
        <button class="footer-btn">
            <span class="footer-btn-text">Назад</span>
            <span class="footer-btn-count">36</span>
        </button>
        <div class="footer-btn-block">
            <button class="button-btn">Отправить всю информацию в WhatsApp</button>
            <button class="footer-btn">
                <span class="footer-btn-text">Вперед</span>
                <span class="footer-btn-count">40</span>
            </button>
        </div>
    </div>
</template>

<style scoped>
    .footer {
        display: flex;
        margin-left: 26px;
        margin-right: 26px;
        justify-content: space-between;

    }
    .footer-btn {
        background-color: #FFDE5F;
        border-radius: 8px;
        border: none;
        outline: none;
        display: flex;
        align-items: baseline;
        gap: 8px;
        padding: 8px;
        cursor: pointer;
    }
    .footer-btn:hover {
        background-color: #323338;
    }
    .footer-btn-text {
        color: #323338;
        font-size: 16px;
        font-weight: 600;
    }
    .footer-btn:hover .footer-btn-text {
        color: #fff;
    }
    .footer-btn-count {
        background-color: #FEF7B1;
        padding: 2px 7px;
        color: #323338;
        font-weight: 600;
        border-radius: 8px;
    }
    .footer-btn:hover .footer-btn-count {
        color: #fff;
        background-color: #676879;
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
    .footer-btn-block {
        display: flex;
        gap: 16px;
    }
</style>