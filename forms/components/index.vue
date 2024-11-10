<template>
  <template v-if="type === 'text'">
    <FormInputText @value="value" v-bind="props"/>
  </template>
  <template v-else-if="type === 'password'">
    <FormInputPassword @value="value" v-bind="props"/>
  </template>
  <template v-else-if="type === 'select'">
    <FormInputSelect @value="value" v-bind="props" />
  </template>
  <template v-else>
    Type {{ type }} not found
  </template>
</template>

<script setup lang="ts">
const props = defineProps({
  id: String,
  name: String,
  placeholder: String,
  type: String,
  options: Array,
});

const emit = defineEmits(["value"]);

function value(value: string) {
  emit('value', value, props.id);
}
</script>
