/* eslint-disable no-console */
<template>
    <button :class="isDisabled ? disabledStyle : buttonStyle">
        <svg v-if="isLoading" class="absolute h-8 w-8 animate-spin" xlmns="http://www.w3.org/2000/svg" fill="none"
            viewBox="0 0 24 24">
            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
            <path class="opacity-75" fill="currentColor"
                d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z">
            </path>
        </svg>

        <component :is="iconLeft" :class="['mr-2 h-6 w-6', isLoading && 'invisible']" />
        <span :class="[isLoading && 'invisible']">
            <slot />
        </span>
        <component :is="iconRight" v-if="!isLoading" :class="['ml-2 h-6 w-6', isLoading && 'invisible']"></component>
    </button>
</template>

<script setup>
import { cva } from "class-variance-authority";
import { computed, defineProps } from 'vue';

const props = defineProps({
    iconLeft: Object,
    iconRight: Object,
    isLoading: Boolean,
    isDisabled: {
        type: Boolean,
        default: false,
    },
    as: {
        type: [String, Object],
        default: "button"
    },
    buttonType: {
        type: String,
        validator: (value) => ["primary", "secondary", "error", "ghost"].includes(value),
        default: "primary",
    },
});

const buttonStyle = computed(() => {
    return cva("inline-flex items-center justify-center text-sm rounded-lg min-h-[48px] min-w-[119px] px-3 py-0.5 font-semibold", {
        variants: {
            buttonType: {
                primary: "bg-[#0a508c] text-white active:shadow-[inset_0_2px_2px_rgba(0,0,0,0.15)] active:border-[2px] active:border-solid active:border-[#0a508c]",
                secondary: "bg-[#141718] text-white hover:bg-[#141718] active:shadow-[inset_0_2px_2px_rgba(0,0,0,0.15)]",
                error: "bg-[#D84C10] text-white hover:bg-[#D84C10] active:shadow-[inset_0_2px_2px_rgba(0,0,0,0.15)]",
                ghost: "bg-transparent border-solid border-2 border-[#E8ECEF] text-black hover:bg-[#E8ECEF] active:shadow-[inset_0_2px_2px_rgba(0,0,0,0.15)]",
            },
        }
    })({
        buttonType: props.buttonType,
    });
});

const disabledStyle = computed(() => {
    return cva("inline-flex items-center justify-center text-sm rounded-md min-h-[48px] px-3 py-0.5 font-semibold", {
        variants: {
            buttonType: {
                primary: "bg-[#0a508c/25] text-[white/25] cursor-not-allowed",
                secondary: "bg-[#141718/25] text-[white/25] cursor-not-allowed",
                error: "bg-[#D84C10/25] text-[white/25] cursor-not-allowed",
                ghost: "bg-transparent border-solid border-2 border-[#F3F5F7/25] text-[black/25] cursor-not-allowed",
            },
        }
    })({
        buttonType: props.buttonType,
    });
});

</script>