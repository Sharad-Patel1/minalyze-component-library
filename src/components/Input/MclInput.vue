/* eslint-disable no-console */
<template>
    <template v-if="this.$props.isDark === true">
        <div class="input-dark">
            <div class="icon">
                <img class="iconImage" :src="icon" alt="icon" />
            </div>
            <input class="textInput-dark" :placeholder="placeholder" />
        </div>
    </template>
    <template v-else>
        <div class="input">
            <div class="icon">
                <img class="iconImage" :src="icon" alt="icon" />
            </div>
            <input class="textInput" :placeholder="placeholder" />
        </div>
    </template>
</template>

<script setup>

import { defineProps } from "vue";

const props = defineProps({
    placeholder: {
        type: String,
        required: true,
    },
    icon: {
        required: true,
    },
    isDark: {
        type: Boolean,
        default: false,
    },
}); 
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Inter: 500");

.input {
    align-items: center;
    background-color: #f3f5f6;
    border-radius: 12px;
    display: flex;
    gap: 12px;
    /* overflow: hidden; */
    padding: 14px 20px;
    position: relative;
    width: 328px;
    box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.06);
}

.input-dark {
    align-items: center;
    background-color: #141718;
    border-radius: 12px;
    display: flex;
    gap: 12px;
    /* overflow: hidden; */
    padding: 14px 20px;
    position: relative;
    width: 328px;
    box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.06);
}

.icon {
    height: 24px;
    min-width: 24px;
    position: relative;
}

.iconImage {
    height: 24px;
    width: 24px;
    /* left: 2px; */
    position: absolute;
}

.textInput {
    font-size: 20px;
    outline: none;
    border: none;
    background-color: #f3f5f6;
    color: #6c717480;
    flex: 1;
}

.textInput-dark {
    font-size: 20px;
    outline: none;
    border: none;
    background-color: #141718;
    color: #6c7174;
    flex: 1;
}

input::placeholder {
    color: #6c717480;
}
</style>