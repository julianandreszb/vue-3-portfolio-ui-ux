<script setup lang="ts">
import type { IButton } from '@/utils/typeScriptDefinitions/IButton'
import { reactive } from 'vue'

const props = withDefaults(defineProps<IButton>(), {
  size: 'md',
  hierarchy: 'Primary',
  state: 'Default'
})

const classObject = reactive({
  'btn-primary': props.hierarchy === 'Primary',

  'btn-sm': props.size === 'sm',
  'btn-md': props.size === 'md',
  'btn-lg': props.size === 'lg',
  'btn-xl': props.size === 'xl',
  'btn-2xl': props.size === '2xl'
})
</script>

<template>
  <button :class="classObject">
    <slot></slot>
  </button>
</template>

<style scoped lang="scss">
@use 'src/assets/styles/text-styles';

button {
  border-radius: 8px;

  &:hover {
    cursor: pointer;
  }
}

.btn-primary {
  background-color: var(--button-primary-bg);
  color: var(--button-primary-fg);
  border: 0.1rem solid var(--button-primary-border);

  &:hover {
    background-color: var(--button-primary-bg_hover);
    color: var(--button-primary-fg_hover);
    border: 0.1rem solid var(--button-primary-border_hover);
  }
}

.btn-sm {
  @include text-styles.text-sm-semibold;
  height: 3.6rem;
  padding-block: 0.8rem;
  padding-inline: 1.2rem;
}

.btn-md,
.btn-lg,
.btn-xl {
  @include text-styles.text-md-semibold;
}

.btn-md {
  height: 4rem;
  padding-block: 1rem;
  padding-inline: 1.4rem;
}

.btn-lg {
  height: 4.4rem;
  padding-block: 1rem;
  padding-inline: 1.6rem;
}

.btn-xl {
  height: 4.8rem;
  padding-block: 1.2rem;
  padding-inline: 1.8rem;
}

.btn-2xl {
  @include text-styles.text-lg-semibold;
  height: 6rem;
  padding-block: 1.6rem;
  padding-inline: 2.2rem;
}
</style>
