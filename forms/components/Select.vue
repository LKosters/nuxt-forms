<template>
  <div :class="'input input_' + id + ' ' + type">
    <label :for="id">
      {{ name }}
    </label>
    <select
      :id="id"
      :name="id"
      v-model="value"
      @change="handleChange"
    >
      <option selected value="">{{ placeholder }}</option>
      <option
        v-for="option in options"
        :value="option.value"
      >
        {{ option.title }}
      </option>
    </select>
  </div>
</template>

<script setup lang="ts">
const props = defineProps({
  id: String,
  name: String,
  placeholder: String,
  type: String,
  options: Array,
});

const value = ref();

const emit = defineEmits(["value"]);

function handleChange() {
  emit('value', value.value);
}
</script>
