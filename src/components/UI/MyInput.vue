<template>
  <input
      :value="modelValue"
      @input="updateInput"
      type="text"
      class="input"
  />
</template>

<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
.input{

  border: 1px solid turquoise;
  padding: 10px 15px;
  margin: 0;
  width:80%;
  border-radius: 8px 0 0 8px;
}
</style>