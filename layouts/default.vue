<template>
  <v-app dark>
    <v-navigation-drawer v-model="drawer" :mini-variant="miniVariant" app>
      <v-list class="pa-0">
        <v-list-item
          style="cursor: pointer"
          @click.stop="miniVariant = !miniVariant"
        >
          <v-list-item-action>
            <v-icon
              >mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon
            >
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="title" />
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer padless inset app absolute="false">
      <v-col class="text-center"
        >&copy; {{ new Date().getFullYear() + ' ' + title }}
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      drawer: true,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
      miniVariant: true,
      title: "Healin' House",
    }
  },
}
</script>

<style>
html {
  overflow-y: auto;
}
</style>
