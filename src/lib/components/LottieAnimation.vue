<template>
  <div class="flex justify-center items-center">
    <div class="max-w-[500px]" :class="uniqueContainerClassName"></div>
  </div>
</template>

<script setup lang="ts">
import lottie from "lottie-web";
import { computed, onMounted } from "vue";

const props = withDefaults(
  defineProps<{
    containerClassName: string;
    startOnInit: boolean;
    loop: boolean;
    json: string;
  }>(),
  {
    startOnInit: true,
    loop: true,
  }
);

const start = () => {
  const container = document.querySelector(
    `.${uniqueContainerClassName.value}`
  );
  if (!container) return;
  lottie.loadAnimation({
    container,
    renderer: "svg",
    loop: props.loop,
    autoplay: true,
    path: props.json,
  });
};

const uniqueContainerClassName = computed(() => {
  return (
    props.containerClassName ||
    `lottie-animation-container-${crypto.randomUUID()}-${Math.floor(
      Math.random() * 100
    )}`
  );
});

onMounted(() => {
  if (props.startOnInit) {
    start();
  }
});
</script>
