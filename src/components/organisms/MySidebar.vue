<template>
  <v-navigation-drawer v-model="state.isShow" app>
    <v-list>
      <v-list-subheader>REPORTS</v-list-subheader>
      <template v-if="items.length">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :value="item"
          active-color="primary"
        >
          <v-list-item-avatar class="mr-2">
            <v-icon :icon="item.icon"></v-icon>
          </v-list-item-avatar>
          <v-list-item-title v-text="item.text"></v-list-item-title>
        </v-list-item>
      </template>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
import { reactive, watch } from 'vue';

export default {
  name: 'MySidebar',

  props: {
    isShow: {
      type: Boolean,
      default: false,
    },
    items: {
      type: Array,
      default: () => [],
    },
  },

  setup(props) {
    const state = reactive({
      isShow: false,
    });

    // TODO: watchエラー出る。分からない
    watch(props.isShow, (newVal) => {
      state.isShow = newVal;
    });

    return {
      state,
    };
  },
};
</script>
