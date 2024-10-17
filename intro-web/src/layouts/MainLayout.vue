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
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Web App
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Links Essencias
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

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

const linksList = [
  {
    title: 'Linkedin',
    caption: 'linkedin.com/in/anthony-c-silva',
    icon: 'school',
    link: 'https://www.linkedin.com/in/anthony-c-silva-844619186'
  },
  {
    title: 'Github',
    caption: 'github.com/anthony-c-silva',
    icon: 'code',
    link: 'https://github.com/anthony-c-silva'
  },
  {
    title: 'Whatsapp',
    caption: 'chat.whatsapp.com',
    icon: 'chat',
    link: 'https://api.whatsapp.com/message/A7BDLAAKRCP7F1?autoload=1&app_absent=0'
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
