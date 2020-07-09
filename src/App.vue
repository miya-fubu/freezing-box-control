<template>
  <v-app>
    <v-app-bar color="blue" dark dense>
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
      <v-toolbar-title>冷蔵庫賞味期限管理くん(仮)</v-toolbar-title>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" absolute tempoirary>
      <v-list nav dense>
        <v-list-item-group active-class="deep-purple--text text--accent-4">
          <v-list-item @click="transPage('home')">
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>
          <v-list-item @click="transPage('list')">
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Mylist</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "App",
  components: {},

  data: () => ({
    drawer: false
  }),

  methods: {
    transPage(url: string) {
      this.$router.push("/" + url);
    }
  }
});
</script>
