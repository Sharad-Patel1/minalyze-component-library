<template>
    <div :class="this.$props.isSelected ? selectedBoxStyle : boxStyle">
        <div class="shrink-0">
            <div :class="tagStyle" />
        </div>
        <div class="flex-1 space-y-2 min-w-0">
            <h2 :class="titleStyle">
                {{ this.$props.title }}
            </h2>
        </div>
    </div>
</template>


<script>
import { cva } from 'class-variance-authority';

export default {
    props: {
        title: {
            type: String,
            required: true,
        },
        isDark: Boolean,
        tag: {
            type: String,
            validator: (value) => ["blue", "violet", "orange", "purple", "green"].includes(value),
            default: "blue",
        },
        isSelected: Boolean,
    },
    computed: {
        boxStyle() {
            return "flex px-4 py-2 rounded-md space-x-3";
        },

        selectedBoxStyle() {
            return cva("flex px-4 py-2 rounded-md space-x-2", {
                variants: {
                    tag: {
                        blue: "bg-dodger-100",
                        violet: "bg-violet-100",
                        orange: "bg-orange-100",
                        purple: "bg-veronica-100",
                        green: "bg-sugus-100",
                    },
                }
            })({
                tag: this.$props.tag,
            });
        },

        tagStyle() {
            return cva("w-3 h-3 rounded-[4px] mt-[55%]", {
                variants: {
                    tag: {
                        blue: "bg-dodger-500",
                        violet: "bg-velvet-500",
                        orange: "bg-mandarin-500",
                        purple: "bg-veronica-500",
                        green: "bg-sugus-500",
                    },
                }
            })({
                tag: this.$props.tag,
            });
        },

        titleStyle() {
            return cva(" mx-4 font-bold ", {
                variants: {
                    isDark: {
                        true: "text-white",
                        false: "text-black",
                    },
                },
            })({
                isDark: this.$props.isDark,
            });
        },
    },

    methods: {

    },
    data() { }
}
</script>
<style lang="">
    
</style>