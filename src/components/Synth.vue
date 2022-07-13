<template>
    <Keyboard @playnote="playTone" />
    <WaveFormSelector @picked="selectWaveForm" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Keyboard from './Keyboard.vue'
import WaveFormSelector from './WaveFormSelector.vue'
export default defineComponent({
    components : { Keyboard, WaveFormSelector },
    setup() {
        const audioContext = new window.AudioContext
        const mainGainNode = audioContext.createGain()
        mainGainNode.connect(audioContext.destination)
        mainGainNode.gain.value = 1
        const waveForm = ref('square')
        const playTone = (freq: number) => {
            const osc = audioContext.createOscillator()
            osc.type = waveForm.value as OscillatorType
            osc.frequency.setValueAtTime(freq, audioContext.currentTime)
            osc.connect(mainGainNode)
            osc.start()
            setTimeout(() => {
                osc.stop()
            }, 100)
        }
        const selectWaveForm = (form: string) => {
            console.log('setting wave form : ', form);
            
            waveForm.value = form
        }
        return { playTone, selectWaveForm }
    }
})
</script>