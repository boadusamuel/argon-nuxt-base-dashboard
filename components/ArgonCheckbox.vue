<template>
  <div class="form-check">
    <input
      :id="id"
      class="form-check-input"
      type="checkbox"
      :name="name"
      :checked="checked"
      @change="toggleChecked"
    />
    <label :for="id" class="custom-control-label" :class="$attrs.class">
      <slot />
    </label>
  </div>
</template>

<script>
export default {
  name: "ArgonCheckbox",
  props: {
    name: {
      type: String,
      default: "",
    },
    id: {
      type: String,
      default: "",
    },
    checked: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    toggleChecked() {
      this.$emit("update:checked", !this.checked);
    },
  },
};
</script>
