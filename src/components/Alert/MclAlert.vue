<template>
    <div v-if="this.$data.show" :class="alertBox">
        <div class="shrink-0">
            <component :is="icon" :class="iconStyle" />
        </div>
        <div class="flex-1 space-y-2 min-w-0">
            <h2 v-if="this.$props.title" :class="titleStyle">
                {{ this.$props.title }}
            </h2>
            <div :class="messageStyle">
                <slot />
            </div>
        </div>
        <div class="shrink-0">
            <button :title="this.$props.closeLabel" :aria-label="closeLabel" :class="closeButton" @click="close()">
                <XMarkIcon class="2-6 h-6" />
            </button>
        </div>
    </div>
</template>


<script>
import {
    InformationCircleIcon,
    XMarkIcon,
    CheckCircleIcon,
    ExclamationTriangleIcon,
    ExclamationCircleIcon,
} from "@heroicons/vue/20/solid/index.js";

import { cva } from "class-variance-authority";

export default {
    name: "Alert",
    props: {
        alertType: {
            type: String,
            validator(value) {
                return ["information", "success", "error", "warning"].includes(value);
            },
            default: "info",
        },
        title: String,
        message: String,
        onClose: Function,
        closeLabel: {
            type: String,
            default: "Dismiss",
        },
    },

    components: {
        InformationCircleIcon,
        XMarkIcon,
        CheckCircleIcon,
        ExclamationCircleIcon,
        ExclamationTriangleIcon,
    },

    data() {
        return {
            iconTarget: null,
            show: true,
        }
    },

    computed: {
        alertBox() {
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
                alertType: this.$props.alertType,
            });
        },

        iconStyle() {
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
                alertType: this.$props.alertType,
            });
        },

        icon() {
            const icons = {
                information: InformationCircleIcon,
                success: CheckCircleIcon,
                error: ExclamationCircleIcon,
                warning: ExclamationTriangleIcon,
            };

            return icons[this.$props.alertType];
            console.log(this.$props.alertType);
        },

        titleStyle() {
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
                alertType: this.$props.alertType,
            });
        },

        messageStyle() {
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
                alertType: this.$props.alertType,
            });
        },

        closeButton() {
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
                alertType: this.$props.alertType,
            });
        },



    },

    methods: {

        show() {
            this.$data.show = true;
        },

        close() {
            if (this.$props.onClose == null) {
                this.$data.show = false;
            }
            else {
                if (this.$props.onClose) {
                    this.$props.onClose();
                }
            }
        }
    }

}
</script>


<style lang="">
    
</style>