<template>
  <v-app>
    <v-content>
        <v-navigation-drawer app dark v-model="show" class="pt-12 pl-4 mr-12">
          <div class="text-center" >
            <v-avatar size="100" >
              <img :src="profilePic" alt="avatar">
            </v-avatar>
          </div>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              {{name}}
            </v-list-item-title>
            <v-list-item-subtitle>
              {{status}}
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list
          dense
          nav
        >
          <v-list-item>
            <v-list-item-icon>
              <span class="group pa-2">
                <v-icon>mdi-home</v-icon>
              </span>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title><v-btn text to="/">Home</v-btn></v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list-item>

            <v-list-item-icon>
              <v-icon class="ml-3">mdi-pencil</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title><v-btn text to="/about">About</v-btn></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list> 
        <div class="pa-4 ml-6 mt-8">
          <v-btn class='mr-8' outlined to="">{{loginStatus}}</v-btn>
        </div>
        <div class="pa-4 ml-6">
          <v-btn class="mr-8" outlined to="/signup">{{signupStatus}}</v-btn>
        </div>
          
      
        
     
        
      </v-navigation-drawer>
   
    
    <v-app-bar dark>

      <v-app-bar-nav-icon class=""  @click.native.stop="show=!show" dark></v-app-bar-nav-icon>
    
    
    
      <v-toolbar-title>REGISTRATION</v-toolbar-title>

      <v-spacer></v-spacer>
      

      <v-btn icon class='mr-12'>
        <v-icon >mdi-magnify</v-icon>
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
  
  data: () => ({
    show: true,
    signupStatus: 'Sign up',
    loginStatus: 'Log In',
    profilePic: './components/logo.png',
    name : '',
    status : '',
    
  }),
  computed:()=>({
    // profileStatus: function () {
    //   // if(this.name !=''){
        
    //   //   return true
    //   // }else{
    //   //   alert('false')
    //   //   return false
    //   // }
     
    // }
  }),
});
</script>
