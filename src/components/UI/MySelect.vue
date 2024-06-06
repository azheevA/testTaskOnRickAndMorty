<template>
  <div>
    <select :value="selectedValue" @change="changeOption">
      <option disabled value="" class="option">Выберите из списка</option>
      <option
          class="option"
          v-for="option in options"
          :key="option.value"
          :value="option.value"
      >
        {{ option.name }}
      </option>
    </select>
    <button @click="applyFilter">Принять</button>
  </div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  name: 'MySelect',
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: () => [],
    },
  },
  setup(props, { emit }) {
    const selectedValue = ref(props.modelValue);

    const changeOption = (event) => {
      selectedValue.value = event.target.value;
    };

    const applyFilter = () => {
      emit('update:modelValue', selectedValue.value);
    };

    watch(() => props.modelValue, (newVal) => {
      selectedValue.value = newVal;
    });

    return {
      selectedValue,
      changeOption,
      applyFilter,
    };
  },
};
</script>

<style scoped>
select {
  border-radius: 0 8px 0 0;
  background: linear-gradient(-45deg, #1e0303, #061033);
  color: turquoise;
  width: 170px;
  height: 20px;
  text-align: center;
  font-size: 14px;
}
.option {
  border-radius: 0 0 8px 8px;
  background: #061033;
}
button {
  border-radius: 0 0 8px 0;
  border-color: rgba(255, 255, 255, 0.6);
  background: linear-gradient(45deg, #1e0303, #061033);
  color: turquoise;
  width: 170px;
  height: 20px;
  text-align: center;
  margin-top: 0;
  font-size: 14px;
}
</style>
