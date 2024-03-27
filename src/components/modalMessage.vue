<template>
    <div v-if="isOpen" class="modal" @click.self="closeModal">
        <div class="modal-content" @click.stop>
            <header>
                <div class="header-block">
                    <span class="title">Запланировать звонок</span>
                    <span class="text">Выберите интересующую вас дату</span>
                </div>
                <span class="close" @click="closeModal">
                    <svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M7.4251 7.975L2.5251 12.875C2.34176 13.0583 2.10843 13.15 1.8251 13.15C1.54176 13.15 1.30843 13.0583 1.1251 12.875C0.941764 12.6917 0.850098 12.4583 0.850098 12.175C0.850098 11.8917 0.941764 11.6583 1.1251 11.475L6.0251 6.575L1.1251 1.675C0.941764 1.49167 0.850098 1.25833 0.850098 0.975C0.850098 0.691667 0.941764 0.458333 1.1251 0.275C1.30843 0.0916663 1.54176 0 1.8251 0C2.10843 0 2.34176 0.0916663 2.5251 0.275L7.4251 5.175L12.3251 0.275C12.5084 0.0916663 12.7418 0 13.0251 0C13.3084 0 13.5418 0.0916663 13.7251 0.275C13.9084 0.458333 14.0001 0.691667 14.0001 0.975C14.0001 1.25833 13.9084 1.49167 13.7251 1.675L8.8251 6.575L13.7251 11.475C13.9084 11.6583 14.0001 11.8917 14.0001 12.175C14.0001 12.4583 13.9084 12.6917 13.7251 12.875C13.5418 13.0583 13.3084 13.15 13.0251 13.15C12.7418 13.15 12.5084 13.0583 12.3251 12.875L7.4251 7.975Z"/>
                    </svg>
                </span>
            </header>
            <select class="select" v-model="selectedDate">
                <option v-for="date in dates" :key="date">{{ formatDate(date) }}</option>
            </select>
            <button class="footer-btn">
                <span class="footer-btn-text">Запланировать</span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            isOpen: false,
            selectedDate: null,
            dates: []
        }
    },
    mounted() {
        this.fillDatesArray();
        const today = new Date();
        this.selectedDate = this.formatDate(today);
    },
    methods: {
        openModal(e) {
            this.isOpen = e;
        },
        closeModal() {
            this.isOpen = false;
        },
        fillDatesArray() {
            const currentDate = new Date();
            for (let i = 0; i < 14; i++) {
                const newDate = new Date(currentDate);
                newDate.setDate(newDate.getDate() + i);
                this.dates.push(newDate);
            }
        },
        formatDate(date) {
            // Функция для форматирования даты в виде "dd/mm/yyyy"
            const day = String(date.getDate()).padStart(2, '0');
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const year = date.getFullYear();
            return `${day}/${month}/${year}`;
        }
    }
}
</script>

<style scoped>
.modal {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.4);
    z-index: 1;
    overflow: auto;
}
.modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 20%;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
    gap: 32px;
}

.modal-content header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
}
.header-block {
    display: flex;
    flex-direction: column;
}
.title {
    color: #323338;
    font-weight: 500;
    font-size: 18px;
}
.text {
    color: #404040;
    font-size: 14px;
    font-weight: 600;
}
.close svg {
    fill: #C5C7D0;
    cursor: pointer;
}
.close:hover svg {
    fill: #323338;
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
    align-self: end;
    width: 45%;
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
.select {
    padding: 10px;
    border: 1px solid rgba(0, 0, 0, 0.56);
    border-radius: 6px;
}

</style>