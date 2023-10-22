<template>
  <NuxtLink class="nav-link" :class="isActive ? 'active' : ''" :to="to" style="width: 100%">
    <div
        class="icon icon-shape icon-sm text-center d-flex align-items-center justify-content-center"
    >
      <slot></slot>
    </div>
    <span class="nav-link-text">{{ text }}</span>
  </NuxtLink>
  <div class="''">

  </div>
</template>
<script setup>
defineProps({
  to: {
    type: [Object, String],
    required: true,
  },
  isActive: {
    type: Boolean,
    required: false,
  },
  text: {
    type: String,
    required: true,
  },

});
</script>
