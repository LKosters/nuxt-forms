<template>
  <div class="p-20">
    <div>
      <h1 class="text-3xl font-black mb-10">Nuxt Forms</h1>
      <div>
        <FormInput
          v-for="input in inputs"
          v-bind="input"
          @value="invokeValue"
        />
      </div>
    </div>
    {{ formValue }}
  </div>
</template>

<script setup lang="ts">
const inputs = ref([
  {
    "id": "email",
    "name": "Email",
    "placeholder": "email",
    "type": "text",
  },
  {
    "id": "password",
    "name": "Password",
    "placeholder": "***",
    "type": "password",
  },
  {
    "id": "rating",
    "name": "Rate your day",
    "placeholder": "0 - 5",
    "type": "select",
    "options": [
      {
        title: "1 star",
        value: "1",
      },
      {
        title: "2 star",
        value: "2",
      },
      {
        title: "3 star",
        value: "3",
      },
      {
        title: "4 star",
        value: "4",
      },
      {
        title: "5 star",
        value: "5",
      }
    ]
  },
]);

const formValue = ref({
  "email": "",
  "password": "",
  "rating": "",
});

function invokeValue(value: string, id: string) {
  if (id in formValue.value) {
    formValue.value[id] = value;
  }
}
</script>
