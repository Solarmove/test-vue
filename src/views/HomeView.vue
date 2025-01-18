<script setup lang="ts">
import { ref, computed } from 'vue'

type Item = {
  name: string
  msg_content: string
}

const items = ref<Item[]>([
  { name: 'замовник', msg_content: 'Сообщение 1' },
  { name: 'виконавець', msg_content: 'Сообщение 2' },
  { name: 'замовник', msg_content: 'Сообщение 3' },
  { name: 'виконавець', msg_content: 'Сообщение 4' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
  { name: 'замовник', msg_content: 'Сообщение 5' },
])

const messageClasses = computed(() => {
  return items.value.map((_, index) => (index % 2 === 0 ? 'left' : 'right'))
})
</script>

<template>
  <div class="container">
    <div class="header-content">
      <div class="tile">Нора 8</div>
    </div>
    <div class="body-content">
      <div class="messages-container">
        <div
          v-for="(item, index) in items"
          :key="item.msg_content"
          :class="['message', messageClasses[index]]"
        >
          <div class="message-header">{{ item.name }}</div>
          <div class="message-content">{{ item.msg_content }}</div>
        </div>
      </div>
    </div>
    <div class="footer-content">
      <div class="input-container">
        <div class="attachments-container">
          <i class="fa-solid fa-paperclip"></i>
        </div>
        <textarea class="text-input" name="msg-input-field" id=""></textarea>
        <div class="send-container">
          <i class="fa-solid fa-paper-plane"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  position: relative;
  display: flex;
  flex-direction: column;
  height: var(--tg-viewport-stable-height);
  /* overflow: hidden; */
  /* gap: 20px; */
}

.header-content {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 22px;
  font-weight: 500;
}

.body-content {
  display: flex;
  align-items: center;
  color: black;
  overflow-y: auto;
  /* flex-grow: 1; */
}

.messages-container {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.message {
  display: flex;
  flex-direction: column;
  margin: 10px 0;
  padding: 10px;
  border-radius: 5px;
}

.message.left {
  align-self: flex-start;
  background-color: #e0f7fa;
}

.message.right {
  align-self: flex-end;
  background-color: #ffebee;
}

.message-header {
  font-weight: bold;
}

.message-content {
  margin-top: 5px;
}

.footer-content {
  position: sticky;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  align-items: center;
  padding-bottom: 20px;
  padding-top: 20px;
  overflow: hidden;
  margin-top: auto;
}

.input-container {
  display: flex;
  justify-content: stretch;
  gap: 10px;
  border-radius: 5px;
}

.text-input {
  flex-grow: 1;
}
</style>
