<template>
  <v-app>
    <v-content>
        <v-navigation-drawer temporary absolute dark v-model="show">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              Application
            </v-list-item-title>
            <v-list-item-subtitle>
              subtext
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list
          dense
          nav
        >
          <v-list-item>
            <v-list-item-group
                v-model="group"
                active-class="deep-purple--text text--accent-4"
            >
              <v-list-item-content>
                <v-list-item-title><v-btn text to="/about">Link 1</v-btn></v-list-item-title>
              </v-list-item-content>

              
              <v-list-item-content>
                <v-list-item-title><v-btn text to="/about">Link 2</v-btn></v-list-item-title>
              </v-list-item-content>

              
              <v-list-item-content>
                <v-list-item-title><v-btn text to="/signup">Sign up</v-btn></v-list-item-title>
              </v-list-item-content>
            </v-list-item-group>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
   
    
    <v-app-bar dark>

      <v-app-bar-nav-icon class="hidden-md-and-up"  @click.native.stop="show=!show"></v-app-bar-nav-icon>
    
    
    
      <v-toolbar-title>REGISTRATION</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn text to="/about">Link 1</v-btn>
        <v-btn text to="/about">Link 2</v-btn>
        <v-btn text to="/about">Link 3</v-btn>
      </v-toolbar-items>
      

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>


     
    </v-app-bar>
    <router-view></router-view>
    </v-content>
    
  </v-app>

  
</template>

<script lang="ts">
import Vue from 'vue';
import HelloWorld from './components/HelloWorld.vue';

export default Vue.extend({
  name: 'App',
  components: {
    HelloWorld,
  },
  data: () => ({
    show: false,
   
  }),
});
</script>
