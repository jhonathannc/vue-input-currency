# Currency Input for Vue3

<p align="center">
<img alt="version" src="https://badgen.net/npm/v/vue-input-currency?color=blue&icon=npm">
<img alt="version" src="https://img.shields.io/github/repo-size/jhonathannc/vue-input-currency?color=blue&label=size&">
<img alt="license" src="https://img.shields.io/github/license/jhonathannc/vue-input-currency?color=blue">
</p>

This package provides a HTML input that formats your number input to any currency using the [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat).

[![](./currency-input.gif)]()

## Installation

You can install the package via composer:

```bash
npm i vue-input-currency
```

## Simple Usage

1. Import in your component and assign a type number value ref of to a value property.
2. The input handles all user inputs and emit the updates on the @update:values

```jsx
<script setup>
  function handleValue({ float, masked }) {
    console.log(float, masked)
  }
</script>

<template>
  <CurrencyInput
    @update:values="handleValue"
    :value="value"
  />
</template>
```

### Properties

You can use the following properties:

|Property|Required|Default|OBS
|-|-|-|-|
|locale|No|pt-BR|[Intl.NumberFormat locales](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#parameters)
| currency|No|BRL|[Intl.NumberFormat currency](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat/NumberFormat#parameters)
| value|No|0|Inital value


This package is open-sourced and licensed under the [MIT license](https://opensource.org/licenses/MIT).