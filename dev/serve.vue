<script>
import Vue from 'vue'
import SpeechRecognition from '@/SpeechRecognition.vue'

export default Vue.extend({
  name: 'ServeDev',
  components: {
    SpeechRecognition
  },
  methods: {
    speechEnd({transcriptions}) {
      console.log(transcriptions)
    }
  }
})
</script>

<template>
  <div id="app">
    <SpeechRecognition lang="en-EN" :white="false" @end="speechEnd"/>
  </div>
</template>
