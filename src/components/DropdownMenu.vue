<script setup lang="ts">
import { ref, watchEffect } from "vue";
const isOpen = ref(false);
const props = defineProps<{
  width?: string;
  bgColor?: string;
  class?: string;
  radius?: string;
  id: string;
}>();
window.addEventListener("click", (e: MouseEvent) => {
  const button = document.getElementById(`td-dropdown-button-${props.id}`);
  const dropdown = document.getElementById(`td-dropdown-${props.id}`);
  if (button && dropdown && e.target)
    if (e.target == button || button.contains(e.target as Node)) {
      isOpen.value = !isOpen.value;
    } else if (
      !(
        e.target == button ||
        e.target == dropdown ||
        button.contains(e.target as Node) ||
        dropdown.contains(e.target as Node)
      )
    ) {
      isOpen.value = false;
    }
});
watchEffect(() => {
  window.dispatchEvent(
    new CustomEvent(
      `${isOpen.value ? "open" : "close"}-td-dropdown-${props.id}`
    )
  );
});
</script>
<template>
  <transition
    enter-active-class="transition ease-in-out duration-500"
    enter-from-class="opacity-0"
    enter-to-class="opacity-100"
    leave-active-class="transition ease-in-out duration-500"
    leave-from-class="opacity-100"
    leave-to-class="opacity-0"
  >
    <div
      :id="`td-dropdown-${id}`"
      v-show="isOpen"
      :class="` absolute p-2 flex items-center justify-center flex-col gap-2 ${$props.class}`"
      :style="`width:${width ?? '128px'};background-color:${
        bgColor ?? 'rgb(55,65,81)'
      };border-radius:${radius ?? '8px'}`"
    >
      <slot />
    </div>
  </transition>
</template>
