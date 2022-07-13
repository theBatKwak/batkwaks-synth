<template>
<div class="flex flex-col">
    <div>
        <input v-model="selectedWave" @change="pickedWave('square')" type="radio" id="square" value="square">
        <label for="square">Square</label>
    </div>
    <div> 
        <input v-model="selectedWave" @change="pickedWave('sine')" type="radio" id="sine" value="sine">
        <label for="sine">sine</label>
    </div>
    <div>
        <input v-model="selectedWave"  @change="pickedWave('sawtooth')" type="radio" id="sawtooth" value="sawtooth"> 
        <label for="sawtooth">sawtooth</label>
    </div>
    <div>
        <input v-model="selectedWave" @change="pickedWave('triangle')" type="radio" id="triangle" value="triangle">
        <label for="triangle">triangle</label>
    </div>
</div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
export default defineComponent({
    emits: ['picked'],
    setup(props, context) {
        const selectedWave = ref('square')
        const pickedWave = (wave: string) => {
            selectedWave.value = wave
            context.emit('picked', wave)
        }
        return { selectedWave, pickedWave }
    }
})
</script>
