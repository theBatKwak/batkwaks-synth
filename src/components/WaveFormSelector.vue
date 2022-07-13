<template>
<div class="flex flex-col bg-slate-700 px-4 py-2 rounded shadow-2xl">
    <h3 class="text-xl mb-2 font-bold">Wave</h3>
    <div class="flex items-center my-1">
        <input v-model="selectedWave" @change="pickWave('square')" class="text-amber-500 mr-2 border-none" type="radio" id="square" value="square">
        <label for="square">
            <base-icon icon="square-wave" :classes="selectedWave === 'square' ? 'stroke-amber-500' : 'stroke-slate-500'" />
        </label>
    </div>
    <div class="flex items-center my-1"> 
        <input v-model="selectedWave" @change="pickWave('sine')" class="text-amber-500 mr-2 border-none" type="radio" id="sine" value="sine">
        <label for="sine">
            <base-icon icon="sine-wave" :classes="selectedWave === 'sine' ? 'stroke-amber-500' : 'stroke-slate-500'" />
        </label>
    </div>
    <div class="flex items-center my-1">
        <input v-model="selectedWave"  @change="pickWave('sawtooth')" class="text-amber-500 mr-2 border-none" type="radio" id="sawtooth" value="sawtooth"> 
        <label for="sawtooth">
            <base-icon icon="sawtooth-wave" :classes="selectedWave === 'sawtooth' ? 'stroke-amber-500' : 'stroke-slate-500'" />
        </label>
    </div>
    <div class="flex items-center my-1">
        <input v-model="selectedWave" @change="pickWave('triangle')" class="text-amber-500 mr-2 border-none" type="radio" id="triangle" value="triangle">
        <label for="triangle">
            <base-icon icon="triangle-wave" :classes="selectedWave === 'triangle' ? 'stroke-amber-500' : 'stroke-slate-500'" />
        </label>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import SawToothWaveIcon from '../assets/icons/sawtooth-wave.svg'
import SinWaveIcon from '../assets/icons/sin-wave.svg'
import SquareWaveIcon from '../assets/icons/square-wave.svg'
import TriangleWaveIcon from '../assets/icons/triangle-wave.svg'
import BaseIcon from "./BaseIcon.vue"
export default defineComponent({
  components: { BaseIcon },
    emits: ['picked'],
    setup(props, context) {
        const selectedWave = ref('square')
        const pickWave = (wave: string) => {
            selectedWave.value = wave
            context.emit('picked', wave)
        }
        return {
            selectedWave,
            pickWave,
            TriangleWaveIcon,
            SawToothWaveIcon,
            SinWaveIcon,
            SquareWaveIcon
        }
    }
})
</script>
