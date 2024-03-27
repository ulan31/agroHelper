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
                <img class="img-block" v-if="messages.length === 0" src="@/assets/logo.svg"/>
                <template v-else>
                    <span class="date">{{ new Intl.DateTimeFormat("ru").format(date) }}</span>

                    <div class="height-auto">
                        <messages-block :message="message"/>
                        <transcript :message="message2"/>
                        <audio-file :src="audioFile" class="mt-0"/>
                        <result1 :result="result1"/>
                        <result2/>
                        <result3/>
<!--                        <messages-block :message="message3" :isShowWhatSapp="false" class="mt-0"/>-->
<!--                        <messages-block :message="message3" :isShowWhatSapp="false" class="mt-0"/>-->
                    </div>



                    <div>
                        <button-level-1 @openModal="openModal"/>
                        <button-level-2 class="mt-16"/>
                        <footer-bottom class="mt-16"/>
                    </div>
                </template>


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
import PulseLoader from 'vue-spinner/src/PulseLoader.vue';
import result1 from "@/components/result1.vue";
import result2 from "@/components/result2.vue";
import result3 from "@/components/result3.vue";
import transcript from "@/components/transcript.vue";

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
        PulseLoader,
        result1,
        result2,
        result3,
        transcript
    },
    data() {
        return {
            loading: false,
            loading1: false,
            leftMessages1: {
                title: 'Сегодняшние сообщения',
                count: ''
            },
            leftMessages2: {
                title: 'Плановые сообщения',
                count: ''
            },
            messages: [],
            message: [],
            audioFile: '',
            result1: '',
            message2: '',
            // message2: [
            //     {title: 'Робот:', text: 'Алло.'},
            //     {title: 'Фермер:', text: 'Алло.'},
            //     {title: 'Робот:', text: 'Здравствуйте, это Сергей из Олсан. Мы закупаем подсолнечник у себя на воротах. Удобно сейчас?'},
            //     {title: 'Фермер:', text: 'Что подсолнечник?'},
            //     {title: 'Робот:', text: 'Мы предлагаем у нас на воротах. Без НДС 25,6 рублей за килограмм, а с НДС это 28,2. Будете продавать?'},
            //     {title: 'Фермер:', text: 'У меня не на чем доставлять его.'},
            // ],
            id: null,
        }
    },
    mounted() {
        this.getIdFromUrl();
        this.getCount();
    },
    methods: {
        getIdFromUrl() {
          const urlParams =  new URLSearchParams(window.location.search);
          const paramValue = urlParams.get("id");
          if(urlParams.has("id")) {
              this.id = paramValue;
          } else {
              this.id = "0d8d2539-6826-441a-9dd1-af24fa219da2";
          }
        },
        async getCount() {
            this.loading = true;
            try {
                const response = await axios.get(`http://172.201.225.48:5003/counters/${this.id}`);
                console.log(response.data);
                if(response?.data) {
                    const { fresh_len, pending_len} = response?.data;
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
            this.loading = true;
            try {
                const response = await axios.get(`http://172.201.225.48:5003/fresh/${this.id}`);
                if(response?.data) {
                    this.messages = response.data.records;
                    this.message = this.messages[0];
                    this.message2 = this.messages[0]?.text;
                    this.audioFile = this.message.url;
                    this.result1 = this.message.responce;
                    this.loading = false;
                }
            } catch (e) {
                this.loading = false;
            }

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
    min-height: 100vh;
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
  .img-block {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 100px;
      height: 100px;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
  }
  .footer-block {
      position: absolute;
      bottom: 30px;
      left: 0;
      right: 0;
  }

@media (max-width: 992px) {
    .height-auto {
        overflow-y: auto;
    }
}
</style>