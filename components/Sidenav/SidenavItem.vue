<template>
  <NuxtLink class="nav-link" :to="to">
    <div
        class="icon icon-shape icon-sm text-center d-flex align-items-center justify-content-center"
    >
      <slot></slot>
    </div>
    <span class="nav-link-text">{{ text }}</span>
  </NuxtLink>
</template>
<script setup>
defineProps({
  to: {
    type: [Object, String],
    required: true,
  },
  miniIcon: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
});
</script>
