<template>
  <main class="main">
    <section class="main-left">
        <logo/>
        <messages/>
        <messages/>
    </section>
    <section class="main-right">
        <span class="date">08/02/2024</span>

        <article class="message">
            <div class="message-block">
                <span class="message-title">Date:</span> <span class="message-text">08/02/2024</span>
            </div>
            <div class="message-block">
                <span class="message-title">Deal_ID:</span> <span class="message-text">12345678</span>
            </div>
            <div class="message-block">
                <span class="message-title">Call_ID:</span> <span class="message-text">12345678</span>
            </div>
            <div class="message-block">
                <span class="message-title">Farmer_ID:</span> <span class="message-text">12345678 (Иван Иванов)</span>
            </div>
            <div class="message-block">
                <span class="message-title">Crop_ID:</span> <span class="message-text">123 (Подсолнечник)</span>
            </div>
            <div class="message-block">
                <span class="message-title">Storage_ID:</span> <span class="message-text">123</span>
            </div>
        </article>
    </section>
  </main>
</template>

<script>
import logo from "@/components/logo.vue";
import messages from "@/components/messages.vue";
export default {
    components: {
        logo,
        messages
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
    align-items: center;
    justify-content: center;
      flex-direction: column;
    width: 1140px;
    margin: 30px;
    background-color: #F5F6F8;
    border: 1px solid #E6E9EF;
  }

  .date {
      font-size: 14px;
      color: #676879;
  }

  .message {
      max-width: 100%;
      background-color: #E6E9EF;
      padding: 16px 10px 16px 10px;
      border-radius: 16px;
  }
  .message-block {
      display: flex;
      align-items: center;
      gap: 5px;
  }
  .message-title {
      font-weight: 500;
      font-size: 14px;
      color: #000;
  }

  .message-text {
      font-size: 14px;
      color: #000;
  }


</style>
<script setup>
</script>