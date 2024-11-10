<template>
  <div :class="'input input_' + id + ' ' + type">
    <label :for="id">
      {{ name }}
    </label>
    <input
      v-model="value"
      @focusout="handleFocusOut"
      :id="id"
      :name="id"
      :placeholder="placeholder"
      type="password"
    />
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  id: String,
  name: String,
  placeholder: String,
  type: String,
});

const value = ref();

const emit = defineEmits(["value"]);

function handleFocusOut() {
  emit('value', value.value);
}
</script>
