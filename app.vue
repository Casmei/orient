<template>
  <div class="flex flex-col xl:flex-row justify-between w-full">
    <Navbar
      @exec="handleClick"
      :show-builder-flow="showBuilderFlow"
      @closing="handleClose"
    />
    <section>
      <FlowSideBar
        v-if="showBuilderFlow"
        @closing="handleClose"
      />

      <FlowData
        v-if="showBuilderFlow"
        @closing="handleClose"
      />
    </section>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Navbar from "./components/layout/navbar.vue";
import FlowSideBar from "./components/builder/BuilderSideContent.vue";
import FlowData from "./components/builder/FlowData.vue";

const showBuilderFlow = ref(false);

function handleClick() {
  showBuilderFlow.value = true;
}

function handleClose() {
  showBuilderFlow.value = false;
}
</script>