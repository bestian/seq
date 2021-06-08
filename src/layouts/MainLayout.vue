<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          數列填空
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          類型
        </q-item-label>
        <q-select v-model="type" :options="types" label="類型" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view :type="type"/>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  data () {
    return {
      leftDrawerOpen: false,
      types: ['d', 'r'],
      type: 'd'
    }
  }
}
</script>

<style type="text/css" scoped="">
  input {
    width: 100px;
  }
</style>
