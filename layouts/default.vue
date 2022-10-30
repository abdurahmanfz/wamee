<template>
  <v-app>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      class="primary elevation-0"
    >
      <v-img max-height="32" max-width="32" src="/favicon.ico" class="mr-1" />
      <v-toolbar-title class="white--text font-weight-bold poppins" v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main style="background: url('7600.jpg'); background-repeat: no-repeat; background-size: cover; background-position: center; background-attachment: fixed;">
      <v-container class="mt-4">
        <nuxt />
      </v-container>
    </v-main>
    <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-footer
      :absolute="!fixed"
      app
    >
      <a target="_blank" href="https://www.instagram.com/abdurahmanfz" class="caption">&copy; @abdurahmanfz</a>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'WaMe'
    }
  }
}
</script>
