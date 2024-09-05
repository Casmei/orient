<template>
  <div class="flex flex-col xl:flex-row justify-between w-full">
    <Navbar
      @exec="handleClick"
      :show-component-flow="showBuilderFlow"
      @closing="handleClose"
      v-motion-slide-left
    />
    <section>
      <FlowSideBar
        v-if="showBuilderFlow"
        @closing="handleClose"
        v-motion-fade
      />

      <PopUpToShowFlowInComputer
        v-if="showBuilderFlow"
        @closing="handleClose"
        v-motion-slide-left
      />
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Navbar from "./components/layout/navbar.vue";
import FlowSideBar from "./components/builder/BuilderSideContent.vue";
import PopUpToShowFlowInComputer from "./components/builder/FlowData.vue";

const showBuilderFlow = ref(false);

function handleClick() {
  showBuilderFlow.value = true;
}

function handleClose() {
  showBuilderFlow.value = false;
}
</script>