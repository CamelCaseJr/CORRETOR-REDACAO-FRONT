<template>
  <q-layout view="hHh lpR fFf">
    <q-header
      bordered
      class="bg-white my-header text-blue-grey-14 q-pt-sm q-pb-sm"
    >
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          color="grey-6"
          icon="menu"
          @click="toggleLeftDrawer"
        />

        <q-avatar>
          <img
            src="https://app.glau.com.vc/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Flogo-192x192.1a71ab0d.png&w=1080&q=75"
          />
        </q-avatar>
        <q-toolbar-title style="tex-size: 5rem"> CamelCase </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <menu-lateral v-model="leftDrawerOpen" />

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import MenuLateral from 'src/components/MenuLateral.vue';
import { defineComponent, ref } from 'vue';

export default defineComponent({
  components: { MenuLateral },
  name: 'MainLayout',

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>

<style scoped lang="scss">
.my-header {
}
</style>
