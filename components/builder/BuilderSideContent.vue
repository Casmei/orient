<template>
  <div class="p-4 fixed top-0 left-0 h-full w-full xl:w-[380px] bg-blue-project text-white z-50 overflow-y-auto">
    <div class="p-6">
      <div class="flex justify-between items-center">
        <div class="flex items-center gap-2">
          <Icon name="material-symbols:rebase" size="32px" />
          <h3 class="text-[18px] font-strong">Fluxo de cobrança</h3>
        </div>
        <button
          @click="toggleState"
          :class="['hover:opacity-90 transition-all rounded-2xl w-18 gap-1 flex items-center justify-between', isActive ? 'bg-green-400' : 'bg-red-400']"
        >
          <span class="ml-2 font-less">{{ isActive ? 'Ativo' : 'Inativo' }}</span>
          <Icon :name="isActive ? 'ion:ellipse' : 'ion:ellipse-outline'" size="22px" />
        </button>
      </div>

      <div class="mt-8">
        <button class="font-less bg-white text-[#7A828A] flex items-center gap-2 rounded-lg px-4 py-[3px]">
          EM TESTE
          <Icon name="material-symbols:close-rounded" class="text-[#7A828A]" />
        </button>
        <div class="relative mt-10">
          <label for="search" class="absolute top-[11px] left-2 text-[#7A828A]">
            <Icon name="ic:baseline-search" size="28" />
          </label>
          <input
            type="text"
            name="search"
            class="w-[294px] h-[46px] text-gray-600 outline-none rounded-lg px-[40px] placeholder-[#7A828A]"
            placeholder="Pesquisar Bloco..."
          />
        </div>
      </div>
      <div v-for="block in blocks" :key="block.type" class="mt-8">
        <IntegrationBlock
          :icon="block.icon"
          :title="block.title"
          :type="block.type"
          @toggle="handleToggle"
        />
        <transition name="slide">
          <Integrations v-if="activeBlock === block.type" v-motion-slide-bottom />
        </transition>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Integrations from '/components/builder/Integrations.vue';
import IntegrationBlock from '/components/builder/IntegrationBlock.vue';

const isActive = ref(true);
const activeBlock = ref(null);

const blocks = [
  { icon: 'ion:md-flash', title: 'Integrações', type: 'integrations' },
  { icon: 'material-symbols:timer', title: 'Gatilhos', type: 'triggers' },
  { icon: 'material-symbols:database', title: 'Dados', type: 'data' },
  { icon: 'material-symbols:share', title: 'Lógica', type: 'logic' },
  { icon: 'material-symbols:video-file', title: 'Arquivos', type: 'files' },
  { icon: 'oui:app-advanced-settings', title: 'Avançado', type: 'advanced' },
  { icon: 'ph:brain-fill', title: 'Inteligência Artificial', type: 'ai' }
];

const toggleState = () => {
  isActive.value = !isActive.value;
  setTimeout(() => close(), 500);
};

const handleToggle = ({ isActive: active, type }) => {
  if (active) {
    activeBlock.value = type;
  } else {
    activeBlock.value = null;
  }
};

const emit = defineEmits(['closing']);
const close = () => emit('closing');
</script>
