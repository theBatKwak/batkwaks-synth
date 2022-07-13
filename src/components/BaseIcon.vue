<template>
    <component
        :is="iconComponent"
        role="img"
        :class="classes"
    />
</template>

<script lang="ts">
import { computed, defineComponent } from "vue"
import SawToothWaveIcon from './icons/SawToothWaveIcon.vue'
import SinWaveIcon from './icons/SinWaveIcon.vue'
import SquareWaveIcon from './icons/SquareWaveIcon.vue'
import TriangleWaveIcon from './icons/TriangleWaveIcon.vue'
const icons: any = {
    'sawtooth-wave': SawToothWaveIcon,
    'sine-wave': SinWaveIcon,
    'square-wave': SquareWaveIcon,
    'triangle-wave': TriangleWaveIcon
}
export default defineComponent({
    props: {
        icon: {
            type: String,
            required: true
        },
        classes: {
            type: String,
            default: ''
        }
    },
    setup(props) {
        const iconComponent = computed(() => {return icons[props.icon]})
        return {
            iconComponent
        }
    }
})
</script>