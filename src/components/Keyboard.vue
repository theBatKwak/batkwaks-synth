<template>
    <div>
        <section class="flex mx-auto">
            <div 
                @click="playTone(tonesFrequencies['C'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Do</div>
            <div 
                @click="playTone(tonesFrequencies['C#'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-gray-700 text-gray-200">Do#</div>
            <div 
                @click="playTone(tonesFrequencies['D'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Ré</div>
            <div 
                @click="playTone(tonesFrequencies['D#'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-gray-700 text-gray-200">Ré#</div>
            <div 
                @click="playTone(tonesFrequencies['E'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Mi</div>
            <div 
                @click="playTone(tonesFrequencies['F'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Fa</div>
            <div 
                @click="playTone(tonesFrequencies['F#'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-gray-700 text-gray-200">Fa#</div>
            <div 
                @click="playTone(tonesFrequencies['G'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Sol</div>
            <div 
                @click="playTone(tonesFrequencies['G#'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-gray-700 text-gray-200">Sol#</div>
            <div 
                @click="playTone(tonesFrequencies['A'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">La</div>
            <div 
                @click="playTone(tonesFrequencies['A#'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-gray-700 text-gray-200">La#</div>
            <div 
                @click="playTone(tonesFrequencies['B'])" 
                class="mx-0.5 cursor-pointer rounded w-10 h-48 bg-white text-gray-700">Si</div>
        </section>
    </div>
</template>
<script lang="ts">
import { defineComponent, onBeforeMount, onBeforeUnmount, getCurrentInstance } from "vue";
import tonesFrequencies from '../config/tonesFrequencies'

export default defineComponent({
setup (props, context) {
    const keyPlay = (e: KeyboardEvent) => {
        switch(e.code) {
            case 'KeyF':
                playTone(tonesFrequencies['C'])
                break
            case 'KeyT':
                playTone(tonesFrequencies['C#'])
                break
            case 'KeyG':
                playTone(tonesFrequencies['D'])
                break
            case 'KeyY':
                playTone(tonesFrequencies['D#'])
                break
            case 'KeyH':
                playTone(tonesFrequencies['E'])
                break
            case 'KeyJ':
                playTone(tonesFrequencies['F'])
                break
            case 'KeyI':
                playTone(tonesFrequencies['F#'])
                break
            case 'KeyK':
                playTone(tonesFrequencies['G'])
                break
            case 'KeyO':
                playTone(tonesFrequencies['G#'])
                break
            case 'KeyL':
                playTone(tonesFrequencies['A'])
                break
            case 'KeyP':
                playTone(tonesFrequencies['A#'])
                break
            case 'Semicolon':
                playTone(tonesFrequencies['B'])
                break
        }
    }
    const playTone = (freq: number) => {
        context.emit('playnote', freq)
    }
    onBeforeMount(() => {
        document.addEventListener('keydown', keyPlay)
    })
    onBeforeUnmount(() => {
        document.removeEventListener('keydown', keyPlay)
    })
    return { playTone, tonesFrequencies, keyPlay }
}
})
</script>