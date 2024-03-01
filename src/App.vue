<template>
    <div>
        <pulse-loader class="loading" v-if="loading" :loading="loading" :color="'#FFDE5F'" :size="'20px'"></pulse-loader>
        <main v-else class="main">
            <section class="main-left">
                <logo/>
                <messages @click="getRecords" :title="leftMessages1.title" :count="leftMessages1.count"/>
                <messages :title="leftMessages2.title" :count="leftMessages2.count"/>
            </section>
            <section class="main-right">
<!--                <img src="@/assets/logo.svg"/>-->
                <span class="date">{{ new Intl.DateTimeFormat("ru").format(date) }}</span>
                <messages-block :message="message1"/>
                <messages-block :message="message2" class="mt-0"/>
                <audio-file class="mt-0"/>
                <messages-block :message="message3" :isShowWhatSapp="false" class="mt-0"/>
                <button-level-1 @openModal="openModal"/>
                <button-level-2 class="mt-16"/>
                <footer-bottom class="mt-16"/>
            </section>
            <modal ref="modal"/>
        </main>
    </div>

</template>

<script>
import logo from "@/components/logo.vue";
import messages from "@/components/messages.vue";
import messagesBlock from "@/components/messagesBlock.vue";
import buttonLevel1 from "@/components/buttonLevel1.vue";
import buttonLevel2 from "@/components/buttonLevel2.vue";
import footerBottom from "@/components/footerBottom.vue";
import modal from "@/components/modalMessage.vue";
import audioFile from "@/components/audoFile.vue";
import axios from "axios";
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'

export default {
    components: {
        logo,
        messages,
        messagesBlock,
        buttonLevel1,
        buttonLevel2,
        footerBottom,
        modal,
        audioFile,
        PulseLoader
    },
    data() {
        return {
            loading: false,
            leftMessages1: {
                title: 'Сегодняшние сообщения',
                count: ''
            },
            leftMessages2: {
                title: 'Плановые сообщения',
                count: ''
            },
            message1: [
                {title: 'Date:', text: '08/02/2024'},
                {title: 'Deal_ID:', text: '12345678'},
                {title: 'Call_ID:', text: '12345678'},
                {title: 'Farmer_ID:', text: '12345678 (Иван Иванов)'},
                {title: 'Crop_ID:', text: '123 (Подсолнечник)'},
                {title: 'Storage_ID:', text: '123'},
            ],
            message2: [
                {title: 'Робот:', text: 'Алло.'},
                {title: 'Фермер:', text: 'Алло.'},
                {title: 'Робот:', text: 'Здравствуйте, это Сергей из Олсан. Мы закупаем подсолнечник у себя на воротах. Удобно сейчас?'},
                {title: 'Фермер:', text: 'Что подсолнечник?'},
                {title: 'Робот:', text: 'Мы предлагаем у нас на воротах. Без НДС 25,6 рублей за килограмм, а с НДС это 28,2. Будете продавать?'},
                {title: 'Фермер:', text: 'У меня не на чем доставлять его.'},
                {title: 'Робот:', text: 'Хорошо, давайте попробую согласовать вам индивидуальную цену.'},
                {title: 'Фермер:', text: 'Ну хорошо, согласовывайте.'},
                {title: 'Робот:', text: 'Тогда вернусь позже с расчетом. До связи.'},
            ],
            message3: [
                {title: 'Результат:', text: 'готов обсуждать продажу по данной или другой цене - нужно рассчитать индивидуальную цену'},
            ]
        }
    },
    mounted() {
        this.getCount();
    },
    methods: {
        async getCount() {
            this.loading = true;
            try {
                const response = await axios.get("https://172.201.225.48:5003/counters/13427");
                console.log(response.data);
                if(response?.data) {
                    const { fresh_len, pending_len} = response?.data;
                    console.log('here');
                    this.loading = false;
                    this.leftMessages1.count = fresh_len;
                    this.leftMessages2.count =  pending_len;
                }
            } catch (e) {
                this.loading = false;
            }

        },
        openModal(e) {
            console.log(e);
            this.$refs.modal.openModal(e);
        },
        async getRecords() {
            const response = await axios.get("https://172.201.225.48:5003/fresh/13427");
            console.log('response', response);
        }
    }
}
</script>

<style>
.loading {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
}
  .main {
    display: flex;
  }

  .main-left {
    height: 100vh;
    flex: 0 1 240px;
    background-color: #F5F6F8;
    border-right: 1px solid #E6E9EF;
  }

  .main-right {
    display: flex;
    flex-direction: column;
    width: 100%;
    margin: 24px 30px 30px 30px;
    background-color: #F5F6F8;
    border: 1px solid #E6E9EF;
    border-radius: 16px;
    overflow-y: auto;
    position: relative;
  }

  .date {
      font-size: 14px;
      color: #676879;
      text-align: center;
      margin-top: 39px;
  }
</style>