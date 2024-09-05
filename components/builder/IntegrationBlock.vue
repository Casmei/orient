<template>
  <div class="flex justify-between items-center">
    <div class="flex items-center gap-2">
      <Icon :name="icon" size="24" />
      <p class="text-[20px] font-less">{{ title }}</p>
    </div>
    <ToggleButton :type="type" @toggle="handleToggle" />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';
import ToggleButton from './ToggleIntegrationsButton.vue';

const props = defineProps({
  icon: String,
  title: String,
  type: String
});

const emit = defineEmits(['toggle']);
const handleToggle = ({ isActive, type }) => {
  emit('toggle', { isActive, type });
};
</script>
