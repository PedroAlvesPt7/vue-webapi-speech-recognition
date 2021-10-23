<template>
  <div @click="toggle ? endSpeechRecognition() : startSpeechRecognition()">
    <img v-if="toggle" src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB3aWR0aD0iMTI4cHgiIGhlaWdodD0iMTI4cHgiIHZpZXdCb3g9IjAgMCAxMjggMTI4IiB2ZXJzaW9uPSIxLjEiPgo8ZyBpZD0ic3VyZmFjZTEiPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDgwLjM5MjE1NyUsMzYuMDc4NDMxJSwzNi4wNzg0MzElKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNjQgODIuMzI4MTI1IEMgNzYuODQ3NjU2IDgyLjMyODEyNSA4Ny4yNjU2MjUgNzEuOTEwMTU2IDg3LjI2NTYyNSA1OS4wNjI1IEwgODcuMjY1NjI1IDIzLjI2NTYyNSBDIDg3LjI2NTYyNSAxMC40MTQwNjIgNzYuODQ3NjU2IDAgNjQgMCBDIDUxLjE1MjM0NCAwIDQwLjczNDM3NSAxMC40MTQwNjIgNDAuNzM0Mzc1IDIzLjI2NTYyNSBMIDQwLjczNDM3NSA1OS4wNjI1IEMgNDAuNzM0Mzc1IDcxLjkxMDE1NiA1MS4xNTIzNDQgODIuMzI4MTI1IDY0IDgyLjMyODEyNSBaIE0gNjQgODIuMzI4MTI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDgwLjM5MjE1NyUsMzYuMDc4NDMxJSwzNi4wNzg0MzElKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gOTUuNDMzNTk0IDM3LjA3ODEyNSBMIDk1LjQzMzU5NCA0NS4yNSBMIDk5LjUxOTUzMSA0NS4yNSBMIDk5LjUxOTUzMSA1OS4wNjI1IEMgOTkuNTE5NTMxIDc4LjY0ODQzOCA4My41ODU5MzggOTQuNTgyMDMxIDY0IDk0LjU4MjAzMSBDIDQ0LjQxNDA2MiA5NC41ODIwMzEgMjguNDgwNDY5IDc4LjY0ODQzOCAyOC40ODA0NjkgNTkuMDYyNSBMIDI4LjQ4MDQ2OSA0NS4yNSBMIDMyLjU2NjQwNiA0NS4yNSBMIDMyLjU2NjQwNiAzNy4wNzgxMjUgTCAyMC4zMDg1OTQgMzcuMDc4MTI1IEwgMjAuMzA4NTk0IDU5LjA2MjUgQyAyMC4zMDg1OTQgODEuNzc3MzQ0IDM3LjczNDM3NSAxMDAuNDkyMTg4IDU5LjkxNDA2MiAxMDIuNTU4NTk0IEwgNTkuOTE0MDYyIDExOS44MjgxMjUgTCAzNS4yODUxNTYgMTE5LjgyODEyNSBMIDM1LjI4NTE1NiAxMjggTCA5Mi43MTg3NSAxMjggTCA5Mi43MTg3NSAxMTkuODI4MTI1IEwgNjguMDg1OTM4IDExOS44MjgxMjUgTCA2OC4wODU5MzggMTAyLjU1ODU5NCBDIDkwLjI2NTYyNSAxMDAuNDkyMTg4IDEwNy42OTE0MDYgODEuNzc3MzQ0IDEwNy42OTE0MDYgNTkuMDYyNSBMIDEwNy42OTE0MDYgMzcuMDc4MTI1IFogTSA5NS40MzM1OTQgMzcuMDc4MTI1ICIvPgo8L2c+Cjwvc3ZnPgo="/>
    <img v-else :style="white ? 'filter: brightness(0) invert(1);' : ''" src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB3aWR0aD0iMTI4cHgiIGhlaWdodD0iMTI4cHgiIHZpZXdCb3g9IjAgMCAxMjggMTI4IiB2ZXJzaW9uPSIxLjEiPgo8ZyBpZD0ic3VyZmFjZTEiPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDAlLDAlLDAlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gNjQgODIuMzI4MTI1IEMgNzYuODQ3NjU2IDgyLjMyODEyNSA4Ny4yNjU2MjUgNzEuOTEwMTU2IDg3LjI2NTYyNSA1OS4wNjI1IEwgODcuMjY1NjI1IDIzLjI2NTYyNSBDIDg3LjI2NTYyNSAxMC40MTQwNjIgNzYuODQ3NjU2IDAgNjQgMCBDIDUxLjE1MjM0NCAwIDQwLjczNDM3NSAxMC40MTQwNjIgNDAuNzM0Mzc1IDIzLjI2NTYyNSBMIDQwLjczNDM3NSA1OS4wNjI1IEMgNDAuNzM0Mzc1IDcxLjkxMDE1NiA1MS4xNTIzNDQgODIuMzI4MTI1IDY0IDgyLjMyODEyNSBaIE0gNjQgODIuMzI4MTI1ICIvPgo8cGF0aCBzdHlsZT0iIHN0cm9rZTpub25lO2ZpbGwtcnVsZTpub256ZXJvO2ZpbGw6cmdiKDAlLDAlLDAlKTtmaWxsLW9wYWNpdHk6MTsiIGQ9Ik0gOTUuNDMzNTk0IDM3LjA3ODEyNSBMIDk1LjQzMzU5NCA0NS4yNSBMIDk5LjUxOTUzMSA0NS4yNSBMIDk5LjUxOTUzMSA1OS4wNjI1IEMgOTkuNTE5NTMxIDc4LjY0ODQzOCA4My41ODU5MzggOTQuNTgyMDMxIDY0IDk0LjU4MjAzMSBDIDQ0LjQxNDA2MiA5NC41ODIwMzEgMjguNDgwNDY5IDc4LjY0ODQzOCAyOC40ODA0NjkgNTkuMDYyNSBMIDI4LjQ4MDQ2OSA0NS4yNSBMIDMyLjU2NjQwNiA0NS4yNSBMIDMyLjU2NjQwNiAzNy4wNzgxMjUgTCAyMC4zMDg1OTQgMzcuMDc4MTI1IEwgMjAuMzA4NTk0IDU5LjA2MjUgQyAyMC4zMDg1OTQgODEuNzc3MzQ0IDM3LjczNDM3NSAxMDAuNDkyMTg4IDU5LjkxNDA2MiAxMDIuNTU4NTk0IEwgNTkuOTE0MDYyIDExOS44MjgxMjUgTCAzNS4yODUxNTYgMTE5LjgyODEyNSBMIDM1LjI4NTE1NiAxMjggTCA5Mi43MTg3NSAxMjggTCA5Mi43MTg3NSAxMTkuODI4MTI1IEwgNjguMDg1OTM4IDExOS44MjgxMjUgTCA2OC4wODU5MzggMTAyLjU1ODU5NCBDIDkwLjI2NTYyNSAxMDAuNDkyMTg4IDEwNy42OTE0MDYgODEuNzc3MzQ0IDEwNy42OTE0MDYgNTkuMDYyNSBMIDEwNy42OTE0MDYgMzcuMDc4MTI1IFogTSA5NS40MzM1OTQgMzcuMDc4MTI1ICIvPgo8L2c+Cjwvc3ZnPgo="/>
  </div>
</template>

<script>
let SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition
let recognition = SpeechRecognition ? new SpeechRecognition() : false

export default {
  name: 'SpeechRecognition',
  props: {
    lang: {
      type: String,
      default: 'en-EN'
    }, 
    white: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      toggle: false,
      runtimeTranscription: '',
      sentences: []
    }
  },
  methods: {
    checkCompatibility () {
      if (!recognition) {
        console.log('Speech Recognition is not available on this browser. Please use Chrome or Firefox')
      }
    },
    endSpeechRecognition () {
      recognition.stop()
      this.toggle = false
      this.$emit('end', { transcriptions: this.sentences.join('') })
      this.sentences = []
    },
    startSpeechRecognition () {
      if (!recognition) {
        console.log('Speech Recognition is not available on this browser. Please use Chrome or Firefox')
        return false
      }
      
      this.toggle = true
      recognition.lang = this.lang
      recognition.interimResults = true

      recognition.addEventListener('result', event => {
        const value = Array.from(event.results).map(result => result[0]).map(result => result.transcript).join('')
        this.runtimeTranscription = value
      })

      recognition.addEventListener('end', () => {
        if (this.runtimeTranscription !== '') {
          this.sentences.push(this.runtimeTranscription)
        }
        this.runtimeTranscription = ''
        this.endSpeechRecognition()
      })

      recognition.start()
      console.log('Starting speech recognition...')
    }
  },
  mounted () {
    this.checkCompatibility()
  }
}
</script>

<style scoped>
  img {
    max-width: 100%;
    max-height: 100%;
  }
</style>