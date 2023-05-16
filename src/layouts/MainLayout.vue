<template>
  <q-layout view="lHh Lpr lff">
    <q-header class="bg-green-5">
      <q-toolbar>
        <q-btn
          flat
          round
          dense
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
        />
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-md-md">
        <div class="text">Luna Todo</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <img src="~assets/bg.jpg" class="header-image absolute-top" />
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area
        style="
          height: calc(100% - 150px);
          margin-top: 150px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item to="/" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section> Luna To-Do </q-item-section>
          </q-item>

          <q-item to="/help" exact clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section> Help </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top bg-green-10" style="height: 147px">
        <div class="drawer-shadow absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="~assets/images.jpg" />
          </q-avatar>
          <div class="text-weight-bold">Luna</div>
          <div>@lunabuelinda</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from 'quasar';

export default {
  name: 'MyLayout',
  data() {
    return {
      leftDrawerOpen: false,
    };
  },
  computed: {
    todaysDate() {
      let timeStamp = Date.now();
      return date.formatDate(timeStamp, 'dddd D MMMM');
    },
  },
};
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.5;
  filter: grayscale(100%);
}
</style>
