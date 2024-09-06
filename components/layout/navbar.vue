<template>
  <nav class="w-full z-40 bg-white" v-motion-slide-left>
    <div
      class="justify-between px-8 text-[#1A202C] font-strong hidden xl:flex"
      :class="{
        'ml-96 ': showBuilderFlow === true,
        'ml-0': showBuilderFlow === false,
      }"
    >
      <div class="flex gap-4">
        <button
          class="p-4 w-32 button-menu"
          @click="handleClick('edit')"
          :class="{ 'border-b-2 border-blue-500': selectedTab === 'edit' }"
        >
          Editor
        </button>
        <button
          class="p-4 w-auto button-menu"
          @click="handleClick('exec')"
          :class="{ 'border-b-2 border-blue-500 ': selectedTab === 'exec' }"
        >
          Execuções
        </button>
        <button
          class="p-4 w-auto button-menu"
          @click="handleClick('config')"
          :class="{ 'border-b-2 border-blue-500': selectedTab === 'config' }"
        >
          Configurações
        </button>
      </div>

      <div class="flex gap-4 items-center">
        <button
          class="flex items-center gap-2 border p-2 px-6 rounded button-menu"
        >
          <Icon name="material-symbols:play-arrow" size="24px" /> Testar Fluxo
        </button>
        <button
          class="bg-[#167CDD] text-white px-8 p-2 rounded flex items-center gap-2 border hover:bg-black"
        >
          <Icon name="material-symbols:save-outline-sharp" size="20px" /> Salvar
        </button>
      </div>
    </div>

    <div class="block xl:hidden font-strong" v-if="!showBuilderFlow">
      <div class="flex justify-around p-4">
        <button
          @click="handleClick('edit')"
          :class="{ 'border-b-2 border-blue-500': selectedTab === 'edit' }"
        >
          Editor
        </button>
        <button @click="handleClick('exec')">Execuções</button>
        <button
          @click="handleClick('config')"
          :class="{ 'border-b-2 border-blue-500': selectedTab === 'config' }"
        >
          Configurações
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref } from "vue"; // Importa a função 'ref' para gerenciamento de estado reativo

// Define as propriedades do componente, aqui 'showComponentFlow' controla o layout visual
const props = defineProps({
  showBuilderFlow: Boolean,
});

// Define os eventos que o componente pode emitir, como 'exec' e 'closing'
const emit = defineEmits(["exec", "closing"]);

// 'selectedTab' é uma ref (reativa) que armazena a aba atualmente selecionada
const selectedTab = ref("");

// Função chamada quando um botão é clicado, atualiza a aba selecionada e emite eventos
function handleClick(tab: string) {
  selectedTab.value = tab; // Atualiza a aba selecionada
  if (selectedTab.value === "exec") {
    emit("exec"); // Emite o evento 'exec' quando a aba "Execuções" é clicada
  } else {
    emit("closing"); // Emite o evento 'closing' para outras abas
  }
}
</script>
