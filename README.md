# vue-webapi-speech-recognition

Microphone icon as a single component (black or white as default and pale red when it's recording) to interact with the Web Speech Recognition Api.

## Install Vue

```bash
npm install vue-webapi-speech-recognition
```

```js
import Vue from 'vue'
import App from './App.vue'

import SpeechRecognition from 'vue-webapi-speech-recognition'

Vue.use(SpeechRecognition)

new Vue({ render: h => h(App) }).$mount('#app')
```

## Usage

```html
<template>
  <SpeechRecognition lang="en-EN" :white="false" @end="speechEnd" class="icon"/>
</template>

<script>
export default {
  methods: {
    speechEnd({transcriptions}) {
      console.log(transcriptions)
    }
  }
}
</script>

<style scoped>
 .icon {
   width: 64px;
   height: 64px;
 }
</style>
```
