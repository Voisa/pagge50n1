<script setup lang="ts">
import { ref } from 'vue';
import { maskOptions } from './utils/subnetCalculator';
import SubnetForm from './components/SubnetForm.vue';
import SubnetResult from './components/SubnetResult.vue';

const ip = ref<string>('');
const mask = ref<string>(maskOptions[24] || '255.255.255.0');
const isShowResult = ref<boolean>(false);

function handleSubmit() {
  isShowResult.value = true;
}
</script>

<template>
  <div class="app">
    <SubnetForm
      v-model:ip="ip"
      v-model:mask="mask"
      @submit="handleSubmit"
    />
    <SubnetResult
      :ip="ip"
      :mask="mask"
      :is-show-result="isShowResult"
    />
  </div>
</template>

<style>
.app {
  max-width: 600px;
  margin: 2rem auto;
  padding: 1rem;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}

.form {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  align-items: center;
  flex-wrap: wrap;
}

.input,
.select,
.button {
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.input {
  flex: 1;
  min-width: 150px;
}

.button {
  background: #f703d6;
  color: rgb(4, 252, 198);
  cursor: pointer;
  border: none;
}

.button:disabled {
  background: #0c0c0c;
  cursor: not-allowed;
}

.result {
  padding: 1rem;
  background: #209397;
  border: 1px solid #dee2e6;
  border-radius: 4px;
  line-height: 1.5;
}

.scary-text {
  color: #dc3545;
  font-weight: bold;
}
</style>