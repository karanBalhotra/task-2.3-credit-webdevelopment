<template>
  <div>
    <form @submit.prevent="submitForm">
      <!-- Text Interpolation -->
      <label>{{ formLabel }}</label>
      <br>
      <!-- Binding HTML class -->
      <input :class="{ error: hasError }" :value="inputValue" @input="updateInputValue" />
      <br>
      <!-- Binding Inline Styles -->
      <button :style="{ backgroundColor: buttonColor }">Submit</button>
      <br>
      <!-- v-model with input -->
      <input type="text" v-model="textInput" />
      <br>
      <!-- v-model with checkbox -->
      <label>
        <input type="checkbox" v-model="isChecked" />
        Checkbox
      </label>
      <br>
      <!-- v-model with radio buttons -->
      <label>
        <input type="radio" v-model="selectedOption" value="option1" />
        Option 1
      </label>
      <label>
        <input type="radio" v-model="selectedOption" value="option2" />
        Option 2
      </label>
      <br>
      <!-- v-model with select -->
      <select v-model="selectedValue">
        <option value="value1">Value 1</option>
        <option value="value2">Value 2</option>
      </select>
      <br>
      <!-- v-model with textarea -->
      <textarea v-model="textareaValue"></textarea>
      <br>
      <!-- Event Handling -->
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Template Syntax
const formLabel = 'Form Label';

// Class and Style Bindings
const hasError = ref(false);
const buttonColor = 'green';

// Form Input Bindings
const inputValue = ref('');
const textInput = ref('');
const isChecked = ref(false);
const selectedOption = ref('option1');
const selectedValue = ref('value1');
const textareaValue = ref('');

// Event Handling
function updateInputValue(event) {
  inputValue.value = event.target.value;
}

function submitForm() 
{
  if (!textInput.value) 
  {
    hasError.value = true;
  } 
  else 
  {
    hasError.value = false;
    console.log('Form submitted!');
    console.log('Input Value:', inputValue.value);
    console.log('Checkbox Value:', isChecked.value);
    console.log('Selected Option:', selectedOption.value);
    console.log('Selected Value:', selectedValue.value);
    console.log('Textarea Value:', textareaValue.value);
  }
}
</script>

