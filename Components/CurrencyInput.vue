<script setup>
import { ref, watch } from "vue";

const emit = defineEmits(["update:values"]);

const props = defineProps({
  locale: {
    type: String,
    default: "pt-BR",
    required: false,
  },
  currency: {
    type: String,
    default: "BRL",
    required: false,
  },
  value: {
    type: [Number, String],
    default: 0,
    required: false,
  },
});

function formatValue({ value }) {
  const currencyFormatter = new Intl.NumberFormat(props.locale, {
    style: "currency",
    currency: props.currency,
  });

  const float = value;
  const masked = currencyFormatter.format(float);

  return { float, masked };
}

const formatPropValue = () => formatValue({ value: props.value }).masked;

const inputValue = ref(formatPropValue());

const updateInputValue = (value) => {
  const { float, masked } = formatValue({ value });
  inputValue.value = masked;
  return { float, masked };
};

const formatInput = (inputEvent) => {
  const value = inputEvent.target.value;

  const numericValue = value.replace(/[^0-9-]/g, "") / 100;

  const values = updateInputValue(numericValue);

  emit("update:values", values);
};

watch(props, () => updateInputValue(props.value));
</script>

<template>
  <input
    type="text"
    id="input-text"
    v-model="inputValue"
    @input="formatInput"
  />
</template>
