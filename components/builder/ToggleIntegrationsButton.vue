<template>
  <button @click="toggle" class="flex items-center mt-2">
    <Icon :name="isActive ? 'ic:twotone-plus' : 'mdi:minus-thick'" size="22" />
  </button>
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    toggle() {
      this.isActive = !this.isActive;
      this.$emit("toggle", { isActive: this.isActive, type: this.type });
    },
  },
};
</script>