<template>
  <div
    class="fixed inset-0 bg-black bg-opacity-40 flex justify-center items-center z-20"
  >
    <div class="bg-white w-7/12 h-1/2 ml-96 p-4 rounded-2xl">
      <div class="flex justify-between">
        <p class="text-lg font-strong">
          Execuções <span class="text-[#7A828A]">#EM TESTE</span>
        </p>
        <button class="text-sm text-gray-600" @click="close">
          <Icon
            name="material-symbols:close-small-outline"
            class="hover:bg-red-800 transition-all"
            size="24"
          />
        </button>
      </div>

      <div class="mt-4 flex gap-2 text-gray-800">
        <select class="mt-4 bg-gray-100 p-2 rounded-lg outline-none">
          <option value="">Qualquer Status</option>
          <option value="">Ativado</option>
          <option value="">Inativo</option>
        </select>

        <div class="relative">
          <label for="start" class="absolute top-[24px] left-2">
            <Icon name="ic:baseline-timer" size="22" />
          </label>
          <select
            class="mt-4 bg-gray-100 p-2 rounded-lg outline-none px-8"
            name="start"
          >
            <option value="">| Inicio</option>
          </select>
        </div>

        <div class="relative">
          <label for="end" class="absolute top-[24px] left-2">
            <Icon name="ic:baseline-timer" size="22" />
          </label>
          <select
            class="mt-4 bg-gray-100 p-2 rounded-lg outline-none px-8 w-48"
            name="end"
          >
            <option value="">| Fim</option>
          </select>
        </div>
      </div>
      <div class="flex justify-between items-center mt-5 px-2 font-less">
        <div class="flex items-center gap-2">
          <Icon name="weui:eyes-on-outlined" />
          <p>8 Aug as 19:58:04</p>
        </div>

        <div class="flex items-center gap-2">
          <Icon name="weui:eyes-on-outlined" />
          <p>em 0.013s | ID#335763</p>
        </div>

        <div>
          <button class="bg-red-200 px-8 rounded" title="visualizar erro">
            error
          </button>
        </div>

        <button class="hover:opacity-90 transition-all">
          <Icon
            name="material-symbols-light:delete-outline"
            size="24"
            class="text-red-800"
          />
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const emit = defineEmits(["closing"]);
function close() {
  emit("closing");
}
</script>