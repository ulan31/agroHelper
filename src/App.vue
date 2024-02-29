<template>
  <main class="main">
    <section class="main-left">
        <logo/>
        <messages/>
        <messages/>
    </section>
    <section class="main-right">
        <span class="date">08/02/2024</span>
        <messages-block/>
        <messages-block class="mt-0"/>
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