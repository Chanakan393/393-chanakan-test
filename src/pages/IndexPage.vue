<template>
  <q-page class="flex flex-center">
    <q-form @submit.prevent="submitForm" @reset.prevent="resetForm" class="q-gutter-md">

      <q-input
        filled
        label="Your name *"
        v-model="form.name"
      />

      <q-input
        filled
        label="Your age *"
        type="number"
        v-model="form.age"
      />

      <q-checkbox
        v-model="form.accept"
        label="I accept the license and terms"
      />

      <div class="row q-gutter-sm">
        <q-btn type="submit" label="Submit" color="primary"/>
        <q-btn type="reset" label="Reset" color="secondary"/>
      </div>

    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { QForm, QInput, QCheckbox, QBtn, QPage } from 'quasar'

const form = ref({
  name: '',
  age: '',
  accept: false
})

function submitForm() {
  if (!form.value.accept) {
    alert('You need to accept the license and terms first')
    return
  }
  if (!form.value.name) {
    alert('Please type something for name')
    return
  }
  if (form.value.age <= 0) {
    alert('Please type a real age')
    return
  }
  alert('Submitted')
}

function resetForm() {
  form.value.name = ''
  form.value.age = ''
  form.value.accept = false
}
</script>