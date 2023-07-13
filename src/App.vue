<template>
  <div class="flex flex-col mt-4 justify-center space-y-4 place-items-center">
    <div class="text-4xl font-bold justify-start">
      Buttons
    </div>
    <div class="space-x-2">
      <MclButton buttonType="primary">New Button</MclButton>
      <MclButton buttonType="secondary">New Button</MclButton>
      <MclButton buttonType="error">New Button</MclButton>
      <MclButton buttonType="ghost">New Button</MclButton>
    </div>

    <div class="space-x-2">
      <MclButton buttonType="primary" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
      <MclButton buttonType="secondary" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
      <MclButton buttonType="error" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
      <MclButton buttonType="ghost" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
    </div>

    <div class="space-x-2">
      <MclButton buttonType="primary" :disabled="true">New Button</MclButton>
      <MclButton buttonType="secondary" :disabled="true">New Button</MclButton>
      <MclButton buttonType="error" :disabled="true">New Button</MclButton>
      <MclButton buttonType="ghost" :disabled="true">New Button</MclButton>
    </div>
  </div>

  <div class="flex flex-col mt-10 justify-center space-y-4 items-center place-items-center">
    <div class="text-4xl font-bold justify-start">
      Alerts
    </div>
    <MclAlert alertType="information" title="Title">Example Alert</MclAlert>
    <MclAlert alertType="success" title="Title">This is a long Example Alert to show you what it can do.</MclAlert>
    <MclAlert alertType="error" title="Title">Example Alert</MclAlert>
    <MclAlert alertType="warning" title="Title">Example Alert</MclAlert>
  </div>

  <div class="flex flex-col mt-10 justify-center space-y-4 items-center place-items-center">
    <div class="text-4xl font-bold ">
      Inputs
    </div>
    <div class="flex flex-row space-x-4">
      <Mclinput placeholder="Email" v-model="emailAddress" :icon="emailIcon" :isDark="false" />
      <Mclinput placeholder="Email" v-model="emailAddress" :icon="emailIcon" :isDark="true" />
    </div>
  </div>


  <div class="flex flex-col mt-10 justify-center items-center space-x-4">
    <div class="text-4xl font-bold mb-4">
      Toggles
    </div>
    <div class="flex flex-row space-x-5">
      <div class="flex flex-col space-y-2">
        <div class="flex flex-row space-x-2">
          <McltoggleSwitch :highlighted="true" :isDark="false" />
          <McltoggleSwitch v-model="toggleState" :highlighted="true" :isDark="false" />
        </div>
        <div class="flex flex-row space-x-2">
          <McltoggleSwitch :highlighted="true" :isDark="true" />
          <McltoggleSwitch v-model="toggleStateDark" :highlighted="true" :isDark="true" />
        </div>
      </div>
      <div class="flex flex-col space-y-2">
        <div class="flex flex-row space-x-2">
          <McltoggleSwitch :isDark="false" />
          <McltoggleSwitch v-model="toggleState" :isDark="false" />
        </div>
        <div class="flex flex-row space-x-2">
          <McltoggleSwitch :isDark="true" />
          <McltoggleSwitch v-model="toggleStateDark" :isDark="true" />
        </div>
      </div>
    </div>
  </div>

  <div class="flex flex-col mt-10 justify-center space-y-4 items-center place-items-center">
    <div class="text-4xl font-bold mb-4">
      SelectBox
    </div>
    <div class="flex flex-row space-x-2">
      <MclBox title="Minalyze" :isDark="false" tag="blue" :isSelected="false" />
      <MclBox title="Minalyze" :isDark="true" tag="blue" :isSelected="true" />
      <MclBox title="Minalyze" :isDark="false" tag="blue" :isSelected="true" />
    </div>

    <div class="flex flex-row space-x-2">
      <MclBox title="Minalyze" :isDark="false" tag="violet" :isSelected="false" />
      <MclBox title="Minalyze" :isDark="true" tag="violet" :isSelected="true" />
      <MclBox title="Minalyze" :isDark="false" tag="violet" :isSelected="true" />
    </div>

    <div class="flex flex-row space-x-2">
      <MclBox title="Minalyze" :isDark="false" tag="orange" :isSelected="false" />
      <MclBox title="Minalyze" :isDark="true" tag="orange" :isSelected="true" />
      <MclBox title="Minalyze" :isDark="false" tag="orange" :isSelected="true" />
    </div>

    <div class="flex flex-row space-x-2">
      <MclBox title="Minalyze" :isDark="false" tag="purple" :isSelected="false" />
      <MclBox title="Minalyze" :isDark="true" tag="purple" :isSelected="true" />
      <MclBox title="Minalyze" :isDark="false" tag="purple" :isSelected="true" />
    </div>

    <div class="flex flex-row space-x-2">
      <MclBox title="Minalyze" :isDark="false" tag="green" :isSelected="false" />
      <MclBox title="Minalyze" :isDark="true" tag="green" :isSelected="true" />
      <MclBox title="Minalyze" :isDark="false" tag="green" :isSelected="true" />
    </div>

    <div class="flex flex-col mt-10 justify-center space-y-4 items-center place-items-center">
      <FlyoutMenu />
    </div>
  </div>
</template>

<script setup>
import MclButton from './components/Button/MclButton.vue';
import MclAlert from './components/Alert/MclAlert.vue';
import MclBox from './components/Box/MclBox.vue';
import McltoggleSwitch from "./components/Switch/MclSwitch.vue"
import Mclinput from "./components/Input/MclInput.vue"
import { emailIcon } from './assets';
import { ref } from 'vue';

let emailAddress = ""

const toggleState = ref(false)
const toggleStateDark = ref(true)
const loading = ref(true)
</script>
