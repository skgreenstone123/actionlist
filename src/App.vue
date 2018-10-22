<template>
  <v-app id="actions">
    <v-navigation-drawer v-model="drawer" permanent app width="220">
    <v-toolbar color="green darken-1" dark flat>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-list>
        <v-list-tile>
          <v-list-tile-title class="title">
            MyGrower
          </v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-toolbar>
    <v-divider></v-divider>
       <v-list dense class="pa-0">
      <v-list-tile
        v-for="item in items" :key="item.title" @click="changeRoute(item.route)">        
        
        <!-- <router-link :to="{ name: item.route }">
        </router-link> -->

        <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <v-badge v-model="show" v-if="item.showBadge" color="deep-purple" overlap>
          <span slot="badge">6</span>
          <v-list-tile-title>{{ item.title }} &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</v-list-tile-title>
          </v-badge>
          <v-list-tile-title v-else>{{ item.title }}</v-list-tile-title>
        </v-list-tile-content>

      </v-list-tile>
    </v-list>
    </v-navigation-drawer>
    <v-toolbar color="green darken-1" dark fixed app>
      <v-toolbar-title>Actions List</v-toolbar-title>
      <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down">      
      <v-btn flat>
          <font-awesome-icon icon="user" />&nbsp;<span style="text-transform: lowercase;">admin@mygrower.com</span>
      </v-btn>            
      <v-btn flat>Logout</v-btn>
      <!-- <router-link to="/login">
            <v-btn flat>Logout</v-btn>        
      </router-link> -->
    </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <v-container fluid fill-height>
        <v-layout justify-center >
          <v-flex text-xs-center>              
              <router-view class="view"></router-view>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer color="green darken-1" dark fixed>
    <v-spacer></v-spacer>
    <div>&copy; {{ new Date().getFullYear() }}&nbsp;&nbsp;</div>
  </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    items: [
      {
        title: "Ticket Applications",
        icon: "dashboard",
        route: "/actionsList",
        showBadge: false
      },
      {
        title: "Ticket Splits",
        icon: "link_off",
        route: "/actionsList",
        showBadge: true
      },
      {
        title: "Settlements",
        icon: "attach_money",
        route: "/actionsList",
        showBadge: false
      },
      {
        title: "Other requests",
        icon: "question_answer",
        route: "/actionsList",
        showBadge: false
      }
    ],
    right: null,
    drawer: null,
    show: true
  }),
  props: {
    source: String
  },
  methods: {
    changeRoute: function(routeNum) {
      console.log(routeNum);
    }
  }
};
</script>
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>