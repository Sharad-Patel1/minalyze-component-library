/* eslint-disable no-console */
<template>
    <div v-if="show" :class="alertBox">
        <div class="shrink-0">
            <component :is="icon" :class="iconStyle" />
        </div>
        <div class="flex-1 space-y-2 min-w-0">
            <h2 v-if="title" :class="titleStyle">
                {{ title }}
            </h2>
            <div :class="messageStyle">
                <slot />
            </div>
        </div>
        <div class="shrink-0">
            <button :title="closeLabel" :aria-label="closeLabel" :class="closeButton" @click="onClose()">
                <XMarkIcon class="w-6 h-6" />
            </button>
        </div>
    </div>
</template>


<script setup>

/**
 * @param [String] alertType [information, success, error, warning, default(information)]
 * @param [String] title [Title for the alert]
 * @param [String] message [Message that is displayed in the alert]
 * @param [Function] onClose [What the alert does onClose]
 * @param [String] closeLabel [The button pressed to trigger the closeFunction, user will also have a "X" on top left to close/ignore]   
 * 
 */
import {
    InformationCircleIcon,
    XMarkIcon,
    CheckCircleIcon,
    ExclamationTriangleIcon,
    ExclamationCircleIcon,
} from "@heroicons/vue/20/solid/index.js";

import { computed, defineProps } from 'vue';

import { cva } from "class-variance-authority";

const props = defineProps({
    alertType: {
        type: String,
        validator(value) {
            return ["information", "success", "error", "warning"].includes(value);
        },
        default: "information",
    },
    title: String,
    onClose: Function,
    closeLabel: {
        type: String,
        default: "Dismiss",
    },
})

let iconTarget = null;
let show = true;


const alertBox = computed(() => {
    return cva("flex p-4 rounded-md space-x-3 mx-[20%]", {
        variants: {
            alertType: {
                information: "bg-blue-100",
                success: "bg-green-100",
                error: "bg-red-100",
                warning: "bg-yellow-100",
            },
        }
    })({
        alertType: props.alertType,
    });
});

const iconStyle = computed(() => {
    return cva("w-8 h-8", {
        variants: {
            alertType: {
                information: "text-blue-700",
                success: "text-green-700",
                error: "text-red-700",
                warning: "text-yellow-700",
            }
        }
    })({
        alertType: props.alertType,
    });
});

const icon = computed(() => {
    const icons = {
        information: InformationCircleIcon,
        success: CheckCircleIcon,
        error: ExclamationCircleIcon,
        warning: ExclamationTriangleIcon,
    };

    return icons[props.alertType];
});

const titleStyle = computed(() => {
    return cva("font-medium", {
        variants: {
            alertType: {
                information: "text-blue-900",
                success: "text-green-900",
                error: "text-red-900",
                warning: "text-yellow-900",
            }
        }
    })({
        alertType: props.alertType,
    });
});

const messageStyle = computed(() => {
    return cva("text-sm", {
        variants: {
            alertType: {
                information: "text-blue-800",
                success: "text-green-800",
                error: "text-red-800",
                warning: "text-yellow-800",
            }
        }
    })({
        alertType: props.alertType,
    });
});

const closeButton = computed(() => {
    return cva("p-0.5 rounded-md -m-1", {
        variants: {
            alertType: {
                information: "text-blue-900/70 hover:text-blue-900 hover:bg-blue-200 active:bg-blue-300",
                success: "text-green-900/70 hover:text-green-900 hover:bg-green-200 active:bg-green-300",
                error: "text-red-900/70 hover:text-red-900 hover:bg-red-200 active:bg-red-300",
                warning: "text-yellow-900/70 hover:text-yellow-900 hover:bg-yellow-200 active:bg-yellow-300",
            }
        }
    })({
        alertType: props.alertType,
    });
});


function onClose() {
    if (props.onClose == null) {
        show = false;
    }
    else {
        if (props.onClose) {
            props.onClose();
        }
    }
}
</script>