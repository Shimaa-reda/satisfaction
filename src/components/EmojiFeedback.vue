<template>
  <div class="emoji-container">
    <h2 class="fw-bold question_Arabic">ما مدى رضاك عن تجربتك؟</h2>
    <h3 class="fw-bold question">How satisfied are you with <br> your experience?</h3>
    <div class="emojis">
      <span @click="increaseCounter('veryAngryCounter')"><img src="../assets/veryangry.png" alt=""></span>
      <span @click="increaseCounter('angryCounter')"><img src="../assets/angry.png" alt=""></span>
      <span @click="increaseCounter('neutralCounter')"><img src="../assets/neutral.png" alt=""></span>
      <span @click="increaseCounter('happyCounter')"><img src="../assets/happy.png" alt=""></span>
      <span @click="increaseCounter('veryHappyCounter')"><img src="../assets/veryhappy.png" alt=""></span>
    </div>
  </div>
</template>

<script setup>
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
.question_Arabic{
  font-family: "CustomArabicFont", sans-serif;
  font-size: 40px;
  
}
.emoji-container {
  text-align: center;
  font-family: sans-serif;
}
.emojis span {
  font-size: 3rem;
  margin: 1rem;
  cursor: pointer;
}
img{
  width: 60px;
  height: 60px;
}
.question{
  font-family: "Poppins", sans-serif;
  font-size: 50px;
  line-height: 1.5;
}
</style>
