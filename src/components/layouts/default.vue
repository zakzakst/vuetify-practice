<template>
  <!-- <v-navigation-drawer v-model="state.drawer" app>
    <v-list>
      <v-list-subheader>REPORTS</v-list-subheader>
      <v-list-item
        v-for="(item, i) in state.items"
        :key="i"
        :value="item"
        active-color="primary"
      >
        <v-list-item-avatar class="mr-2">
          <v-icon :icon="item.icon"></v-icon>
        </v-list-item-avatar>
        <v-list-item-title v-text="item.text"></v-list-item-title>
      </v-list-item>
    </v-list>
  </v-navigation-drawer> -->
  <my-sidebar :is-show="state.drawer" :items="state.items" />

  <v-app-bar app>
    <v-app-bar-nav-icon
      @click="state.drawer = !state.drawer"
    ></v-app-bar-nav-icon>
    <v-toolbar-title>LOGO</v-toolbar-title>
  </v-app-bar>

  <v-main>
    <v-container class="grey lighten-5">
      <v-row>
        <v-col cols="12" md="8" lg="9">
          <slot />
        </v-col>
        <v-col cols="12" md="4" lg="3">
          <p>{{ state.text }}</p>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
import MySidebar from '../organisms/MySidebar';
import { reactive } from 'vue';

export default {
  name: 'LayoutDefault',

  components: {
    MySidebar,
  },

  setup() {
    const state = reactive({
      text: '右カラム',
      drawer: false,
      selectedItem: 1,
      items: [
        { text: 'Real-Time', icon: 'mdi-clock' },
        { text: 'Audience', icon: 'mdi-account' },
        { text: 'Conversions', icon: 'mdi-flag' },
      ],
    });

    return {
      state,
    };
  },
};
</script>
