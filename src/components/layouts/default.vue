<template>
  <div>
    <p>{{ state.text }}</p>
    <slot />
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  name: 'LayoutDefault',

  setup() {
    const state = reactive({
      text: 'test',
    });

    return {
      state,
    };
  },
};
</script>
