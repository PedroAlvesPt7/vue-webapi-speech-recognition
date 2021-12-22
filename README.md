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


MIT License

Copyright (c) 2021 PedroAlvesPt7

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
