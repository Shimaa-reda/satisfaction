<template>
  <div class="export-container">
    <h2>Download Feedback Summary</h2>

    <download-excel
      ref="excelRef"
      :data="exportData"
      name="feedback-report.xlsx"
      :fields="fields"
      type="xlsx">
      <button @click="handleExport">Download Excel</button>
    </download-excel>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import JsonExcel from 'vue-json-excel3'

const excelRef = ref(null)

const fields = {
  Very_Angry: 'Very_Angry',
  Angry: 'Angry',
  Neutral: 'Neutral',
  Happy: 'Happy',
  Very_Happy: 'Very_Happy',
}

const exportData = ref([
  {
    Very_Angry: localStorage.getItem('veryAngryCounter') || 0,
    Angry: localStorage.getItem('angryCounter') || 0,
    Neutral: localStorage.getItem('neutralCounter') || 0,
    Happy: localStorage.getItem('happyCounter') || 0,
    Very_Happy: localStorage.getItem('veryHappyCounter') || 0,
  },
])

function handleExport() {
  // Delay to ensure file downloaded
  setTimeout(() => {
    localStorage.setItem('veryAngryCounter', 0)
    localStorage.setItem('angryCounter', 0)
    localStorage.setItem('neutralCounter', 0)
    localStorage.setItem('happyCounter', 0)
    localStorage.setItem('veryHappyCounter', 0)

   // Reset exportData too if the page remains open
    exportData.value = [
      {
        Very_Angry: 0,
        Angry: 0,
        Neutral: 0,
        Happy: 0,
        Very_Happy: 0,
      },
    ]
  }, 1000) // 1-second delay to download excel
}
</script>

<script>
export default {
  components: {
    DownloadExcel: JsonExcel,
  },
}
</script>

<style>
.export-container {
  text-align: center;
  margin-top: 40px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 5px;
}
</style>
