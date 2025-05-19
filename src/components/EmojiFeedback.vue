<template>
  <div class="emoji-container">
    <h2 class="fw-bold question_Arabic">ما مدى رضاك عن تجربتك؟</h2>
    <h3 class="fw-bold question">How satisfied are you with <br> your experience?</h3>

    <div class="emojis">
      <span @click="handleEmojiClick('veryAngryCounter')"><img src="../assets/veryangry.png" alt=""></span>
      <span @click="handleEmojiClick('angryCounter')"><img src="../assets/angry.png" alt=""></span>
      <span @click="handleEmojiClick('neutralCounter')"><img src="../assets/neutral.png" alt=""></span>
      <span @click="handleEmojiClick('happyCounter')"><img src="../assets/happy.png" alt=""></span>
      <span @click="handleEmojiClick('veryHappyCounter')"><img src="../assets/veryhappy.png" alt=""></span>
    </div>
  </div>
</template>

<script setup>
import Swal from 'sweetalert2'

function handleEmojiClick(counterKey) {
  increaseCounter(counterKey)

  
  Swal.fire({
  html: '<div style="padding-bottom: 20px;">   !شكرا على تعليقك     <br> Thank you for your feedback!</div>',
  icon: 'success',
  showConfirmButton: false,
  timer: 2000
})

}

function increaseCounter(counterKey) {
  let current = localStorage.getItem(counterKey)
  current = current ? parseInt(current) : 0
  localStorage.setItem(counterKey, current + 1)
}
</script>

<style>
@font-face {
  font-family: "CustomArabicFont";
  src: url("@/assets/fonts/ExpoArabic-Bold.otf") format("truetype");
}

.question_Arabic {
  font-family: "CustomArabicFont", sans-serif;
  font-size: 40px;
}

.emoji-container {
  text-align: center;
  font-family: sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  min-height: 100vh; 
}

.emojis {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem;
  margin-top: 2rem;
}

.emojis span {
  font-size: 3rem;
  cursor: pointer;
}

img {
  width: 60px;
  height: 60px;
}

.question {
  font-family: "Poppins", sans-serif;
  font-size: 50px;
  line-height: 1.5;
}

@media (min-width: 768px) and (max-width: 1024px) {
  .question {
    font-size: 36px;
  }

  .question_Arabic {
    font-size: 32px;
  }

  img {
    width: 50px;
    height: 50px;
  }
}

@media (max-width: 767px) {
  .emoji-container {
    padding: 1rem;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .question {
    font-size: 28px;
  }

  .question_Arabic {
    font-size: 24px;
  }

  .emojis {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    gap: 0.5rem;
  }

  img {
    width: 45px;
    height: 45px;
  }
}

</style>
