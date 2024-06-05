<script setup lang="ts">
const props = defineProps<{
  width?: string;
  btnColor?: string;
  class?: string;
  radius?: string;
  id: string;
}>();
</script>
<template>
  <button
    :id="`td-dropdown-button-${props.id}`"
    :class="`text-white cursor-pointer h-10 w-24 flex bg-none justify-center items-center gap-2 transition-all duration-500 ease-in-out rounded-lg border-solid border  ${$props.class}`"
    :style="`background-color:${btnColor ?? 'rgb(55,65,81)'};border-radius:${
      radius ?? '8px'
    }`"
  >
    <slot />
  </button>
</template>
<style></style>
