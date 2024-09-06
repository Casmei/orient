<template>
  <div class="flex justify-between items-center">
    <div class="flex items-center gap-2">
      <!-- Exibe o ícone e o título com espaçamento entre eles -->
      <Icon :name="icon" size="24" />
      <p class="text-[20px] font-less">{{ title }}</p>
    </div>
    <!-- Botão de alternância (toggle), emitindo um evento de toggle ao ser clicado -->
    <ToggleButton :type="type" @toggle="handleToggle" />
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'; // Funções para definir props e eventos
import ToggleButton from './ToggleIntegrationsButton.vue'; // Componente de botão de alternância

// Define as props recebidas pelo componente (ícone, título e tipo)
const props = defineProps({
  icon: String, // Ícone exibido
  title: String, // Título exibido
  type: String   // Tipo usado no componente ToggleButton
});

// Define os eventos que o componente pode emitir, aqui é o 'toggle'
const emit = defineEmits(['toggle']);

// Função que lida com o evento de alternância e emite o evento 'toggle' com os parâmetros 'isActive' e 'type'
const handleToggle = ({ isActive, type }) => {
  emit('toggle', { isActive, type });
};
</script>
