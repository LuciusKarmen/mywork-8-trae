<template>
  <div>
    <h1>猜数字小游戏</h1>
    <p>猜一个1到100的数字：</p>
    <input v-model="guessNumber" type="number" />
    <button @click="checkGuess">猜！</button>
    <p v-if="message">{{message}}</p>
  </div>
</template>
<script setup>
import { ref } from 'vue';
const guessNumber = ref(null);
const message = ref('');
const checkGuess = () => {
  const randomNumber = Math.floor(Math.random() * 100) + 1;
  if (guessNumber.value === randomNumber) {
    message.value = '恭喜你，猜对了！';
  } else if (guessNumber.value < randomNumber) {
    message.value = '你猜小了，请再试一次。';
  } else {
    message.value = '你猜大了，请再试一次。';
  }
};
</script>