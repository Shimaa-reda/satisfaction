<template>
  <div class="export-container">
    <h2>Download Feedback Summary</h2>
    <download-excel
      :data="exportData"
      name="feedback-report.xls"
      :fields="fields"
      type="xls">
      <button>Download Excel</button>
    </download-excel>
  </div>
</template>

<script setup>
import JsonExcel from 'vue-json-excel3'

const exportData = [
  {
    Very_Angry: localStorage.getItem('veryAngryCounter') || 0,
    Angry: localStorage.getItem('angryCounter') || 0,
    Neutral: localStorage.getItem('neutralCounter') || 0,
    Happy: localStorage.getItem('happyCounter') || 0,
    Very_Happy: localStorage.getItem('veryHappyCounter') || 0,
  },
]

const fields = {
  Very_Angry: 'Very_Angry',
  Angry: 'Angry',
  Neutral: 'Neutral',
  Happy: 'Happy',
  Very_Happy: 'Very_Happy',
}

console.log('Very Angry:', localStorage.getItem('veryAngryCounter'));
console.log('Very Happy:', localStorage.getItem('veryHappyCounter'));

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
