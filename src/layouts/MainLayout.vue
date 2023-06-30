<template>
  <q-layout view="hHh lpR fFf">

    <q-header class="bg-pink-11 text-center q-pa-sm text-white">
      <q-toolbar>
        <q-toolbar-title class="text-h4 text-weight-bold">
          JEJENATOR
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script setup>
import { ref } from 'vue'

const leftDrawerOpen = ref(false)

const toggleLeftDrawer = () => {
  leftDrawerOpen.value = !leftDrawerOpen.value

}

</script>
