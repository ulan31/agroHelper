<template>
  <main class="main">
    <section class="main-left">
        <logo/>
        <messages/>
        <messages/>
    </section>
    <section class="main-right">
        <span class="date">08/02/2024</span>
        <messages-block :message="message1"/>
        <messages-block :message="message2" class="mt-0"/>
        <messages-block :message="message3" :isShowWhatSapp="false" class="mt-0"/>
    </section>
  </main>
</template>

<script>
import logo from "@/components/logo.vue";
import messages from "@/components/messages.vue";
import messagesBlock from "@/components/messagesBlock.vue";
export default {
    components: {
        logo,
        messages,
        messagesBlock
    },
    data() {
        return {
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
    }
}
</script>

<style>
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
  }

  .date {
      font-size: 14px;
      color: #676879;
      text-align: center;
      margin-top: 39px;
  }
</style>