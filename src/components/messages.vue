<template>
    <div class="messages">
        <svg class="messages-svg" width="16" height="16" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
            <path d="M3.41667 9.25H9.25V8.41667H3.41667V9.25ZM3.41667 6.75H12.5833V5.91667H3.41667V6.75ZM3.41667 4.25H12.5833V3.41667H3.41667V4.25ZM0.5 14.7308V1.84583C0.5 1.4625 0.628611 1.1425 0.885833 0.885833C1.1425 0.628611 1.4625 0.5 1.84583 0.5H14.1542C14.5375 0.5 14.8575 0.628611 15.1142 0.885833C15.3714 1.1425 15.5 1.4625 15.5 1.84583V10.8208C15.5 11.2042 15.3717 11.5244 15.115 11.7817C14.8578 12.0383 14.5375 12.1667 14.1542 12.1667H3.06417L0.5 14.7308ZM2.70833 11.3333H14.1542C14.2819 11.3333 14.3994 11.28 14.5067 11.1733C14.6133 11.0661 14.6667 10.9486 14.6667 10.8208V1.84583C14.6667 1.71806 14.6133 1.60056 14.5067 1.49333C14.3994 1.38667 14.2819 1.33333 14.1542 1.33333H1.84583C1.71806 1.33333 1.60056 1.38667 1.49333 1.49333C1.38667 1.60056 1.33333 1.71806 1.33333 1.84583V12.7042L2.70833 11.3333Z"/>
            <path d="M1.33333 11.3333V1.33333M3.41667 9.25H9.25V8.41667H3.41667V9.25ZM3.41667 6.75H12.5833V5.91667H3.41667V6.75ZM3.41667 4.25H12.5833V3.41667H3.41667V4.25ZM0.5 14.7308V1.84583C0.5 1.4625 0.628611 1.1425 0.885833 0.885833C1.1425 0.628611 1.4625 0.5 1.84583 0.5H14.1542C14.5375 0.5 14.8575 0.628611 15.1142 0.885833C15.3714 1.1425 15.5 1.4625 15.5 1.84583V10.8208C15.5 11.2042 15.3717 11.5244 15.115 11.7817C14.8578 12.0383 14.5375 12.1667 14.1542 12.1667H3.06417L0.5 14.7308ZM2.70833 11.3333H14.1542C14.2819 11.3333 14.3994 11.28 14.5067 11.1733C14.6133 11.0661 14.6667 10.9486 14.6667 10.8208V1.84583C14.6667 1.71806 14.6133 1.60056 14.5067 1.49333C14.3994 1.38667 14.2819 1.33333 14.1542 1.33333H1.84583C1.71806 1.33333 1.60056 1.38667 1.49333 1.49333C1.38667 1.60056 1.33333 1.71806 1.33333 1.84583V12.7042L2.70833 11.3333Z" stroke-width="0.3"/>
        </svg>
        <span class="messages-title">
            Сегодняшние сообщения
        </span>
        <span class="messages-count">76</span>
    </div>
</template>

<style scoped>
    .messages {
        box-sizing: border-box;
        margin: 24px auto 0;
        padding: 10px 16px;
        display: flex;
        //outline: 1px solid black;
        align-items: center;
        width: 200px;
        justify-content: center;
        gap: 12px;
        cursor: pointer;
        transition: background-color 0.3s ease;
    }
    .messages:hover {
        background-color: #323338;
        border-radius: 6px;
    }
    .messages-svg {
        fill: #676879;
        transition: fill 0.3s ease;
    }
    .messages:hover .messages-svg {
        fill: #fff;
    }
    .messages:hover .messages-title {
        color: #fff;
    }
    .messages-title {
        color: #323338;
        width: 100px;
    }
    .messages:hover .messages-count {
        color: #E6E9EF;
        background-color: #676879;
    }
    .messages-count {
        color: #676879;
        background-color: #E6E9EF;
        border-radius: 4px;
        padding: 2px 7px;
    }
</style>