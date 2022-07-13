<template>
<div class="flex flex-col">
    <div>
        <input v-model="selectedWave" @change="pickedWave('square')" type="radio" id="square" value="square">
        <label for="square">
            <base-icon icon="square-wave" :classes="'stroke-red-500'" />
        </label>
    </div>
    <div> 
        <input v-model="selectedWave" @change="pickedWave('sine')" type="radio" id="sine" value="sine">
        <label for="sine">
            <base-icon icon="sine-wave" :classes="'stroke-red-500'" />
        </label>
    </div>
    <div>
        <input v-model="selectedWave"  @change="pickedWave('sawtooth')" type="radio" id="sawtooth" value="sawtooth"> 
        <label for="sawtooth">
            <base-icon icon="sawtooth-wave" :classes="'stroke-red-500'" />
        </label>
    </div>
    <div>
        <input v-model="selectedWave" @change="pickedWave('triangle')" type="radio" id="triangle" value="triangle">
        <label for="triangle">
            <base-icon icon="triangle-wave" :classes="'stroke-red-500'" />
        </label>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue"
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
        const pickedWave = (wave: string) => {
            selectedWave.value = wave
            context.emit('picked', wave)
        }
        return {
            selectedWave,
            pickedWave,
            TriangleWaveIcon,
            SawToothWaveIcon,
            SinWaveIcon,
            SquareWaveIcon
        }
    }
})
</script>
