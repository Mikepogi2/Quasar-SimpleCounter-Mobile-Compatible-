<template>
  <q-layout view="lHh Lpr lFf" class="bg-white">
    <q-img src="~assets/sunset.jpg" class="fit absolute" style="filter: blur(4px);"/>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

defineOptions({
  name: 'MainLayout'
})

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
