<template>
  <v-app>
    <v-navigation-drawer app temporary v-model="drawler">
      <v-list>
          <v-list-tile
            v-for="link in links"
            :to="link.url"
            :key="link.title">
            <v-list-tile-action>
              <v-icon>{{link.icon}}</v-icon>
            </v-list-tile-action>

            <v-list-tile-content>
              <v-list-tile-title v-text="link.title"></v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
    </v-navigation-drawer>
    <v-toolbar app dark color="primary">
       <v-toolbar-side-icon @click="drawler = !drawler"
        class="hidden-md-and-up"
       >
       </v-toolbar-side-icon>
       <v-toolbar-title>Ad application</v-toolbar-title>
       <v-spacer></v-spacer>
       <v-toolbar-items class="hidden-sm-and-down">
         <v-btn
          v-for="link in links"
          :to="link.url"
          :key="link.title"
          flat
        >
           <v-icon left>{{link.icon}}</v-icon>
           {{link.title}}
         </v-btn>
       </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawler: false,
      links: [
        {title: 'Login', icon: 'lock', url: '/login'},
        {title: 'Registration', icon: 'face', url: '/registration'},
        {title: 'Orders', icon: 'bookmark_border', url: '/orders'},
        {title: 'New ad', icon: 'note_add', url: '/new'},
        {title: 'My ads', icon: 'list', url: '/list'}
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
