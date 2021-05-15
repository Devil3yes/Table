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
          My Quasar App :3
        </q-toolbar-title>
        <div>
          <q-avatar rounded>
            <img src="https://avatars.githubusercontent.com/u/83644544?s=60&amp;v=4" class="rounded-circle" size="20" height="20" width="20">
          </q-avatar>
        </div>
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
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
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

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Quasar',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com',
    icon: 'code',
    link: 'https://github.com/'
  },
  {
    title: 'Icons',
    caption: 'Make Icons',
    icon: 'favorite',
    link: 'https://fonts.google.com/icons?selected=Material+Icons:home&icon.query=+'
  },
  {
    title: 'Table',
    caption: 'Make Tables',
    icon: 'table_chart',
    link: 'https://quasar.dev/vue-components/table#introduction'
  }
];

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
