<template>
<div class="flex flex-col items-center justify-between h-full p-4">
    <div class="flex flex-wrap">
        <WaveFormSelector @picked="selectWaveForm" />
    </div>
    <Keyboard @playnote="playTone" />
</div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Keyboard from './Keyboard.vue'
import WaveFormSelector from './WaveFormSelector.vue'
export default defineComponent({
    components : { Keyboard, WaveFormSelector },
    setup() {
        const audioContext = new window.AudioContext
        // mainGainNode.gain.value = 1
        const waveForm = ref('square')
        const attackTime = ref(0.9)
        const playTone = (freq: number) => {
            const osc = audioContext.createOscillator()
            osc.type = waveForm.value as OscillatorType
            osc.frequency.setValueAtTime(freq, audioContext.currentTime)
            const mainGainNode = audioContext.createGain()
            mainGainNode.gain.cancelScheduledValues(1);
            mainGainNode.gain.setValueAtTime(0, 1);
            mainGainNode.gain.linearRampToValueAtTime(1, 0 + attackTime.value)
            osc.connect(mainGainNode).connect(audioContext.destination)
            osc.start()
            osc.stop(audioContext.currentTime + 1)
        }
        const selectWaveForm = (form: string) => {
            console.log('setting wave form : ', form);
            
            waveForm.value = form
        }
        return { playTone, selectWaveForm }
    }
})
</script>