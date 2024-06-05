<script setup lang="ts">
defineProps<{ btnColor?: string; radius?: string; class?: string }>();
</script>
<template>
  <div
    :class="`w-full min-h-6 cursor-pointer hover:bg-[rgb(80,90,106)] flex justify-start p-2 items-center gap-2.5 text-gray-400 transition-all duration-500 ease-in-out hover:text-gray-300 ${$props.class}`"
    :style="`background-color:${btnColor ?? 'none'};border-radius:${
      radius ?? '8px'
    }`"
  >
    <slot />
  </div>
</template>
<style scoped></style>
