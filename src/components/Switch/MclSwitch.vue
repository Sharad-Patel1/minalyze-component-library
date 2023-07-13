/* eslint-disable no-console */
<template>
    <div v-if="isDark === false">
        <div v-if="highlighted === true" :class="modelValue ? 'bg-[#0084FF]' : 'bg-[#E8ECEF]'" @click="toggle"
            class="w-14 transition-all duration-500 h-8 flex items-center rounded-full p-1">
            <div :class="{ 'translate-x-6': modelValue }"
                class="w-6 h-6 transition-all duration-500 transform bg-white rounded-full shadow-md"></div>
        </div>
        <div v-else @click="toggle"
            class="w-14 transition-all duration-500 h-8 flex items-center rounded-full p-1 bg-[#E8ECEF]">
            <div :class="{ 'translate-x-6': modelValue }"
                class="w-6 h-6 transition-all duration-500 transform bg-white rounded-full shadow-md"></div>
        </div>
    </div>
    <div v-else>
        <div v-if="highlighted === true">
            <div :class="modelValue ? 'bg-[#0084FF]' : 'bg-[#343839]'" @click="toggle"
                class="w-14 transition-all duration-500 h-8 flex items-center rounded-full p-1">
                <div :class="{ 'translate-x-6': modelValue }"
                    class="w-6 h-6 transition-all duration-500 transform bg-white rounded-full shadow-md"></div>
            </div>
        </div>
        <div v-else>
            <div @click="toggle"
                class="w-14 transition-all duration-500 h-8 flex items-center rounded-full p-1 bg-[#343839]">
                <div :class="{ 'translate-x-6': modelValue }"
                    class="w-6 h-6 transition-all duration-500 transform bg-white rounded-full shadow-md"></div>
            </div>
        </div>
    </div>
</template>
  
<script setup>
import { defineProps } from "vue";

const props = defineProps({
    isDark: {
        type: Boolean,
        required: true,
    },
    modelValue: {
        type: Boolean,
    },
    highlighted: {
        type: Boolean,
    }
})

const emit = defineEmits(['update:modelValue']);

function toggle() {
    emit('update:modelValue', !props.modelValue)
}
</script>