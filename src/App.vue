<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app :mobile-breakpoint="768">
      <v-img
        class="pa-4 pt-7"
        src="mountains.png"
        height="170"
        gradient="to top right, rgba(55,236,186,.7), rgba(25,32,72,.7)"
      >
        <v-avatar size="70" class="mb-2">
          <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
        </v-avatar>
        <div class="white--text text-subtitle-1 font-weight-bold">
          Cuneyd Gultekin Kaya
        </div>
        <div class="white--text text-subtitle-2">yaqushuklu_jojuq</div>
      </v-img>
      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="primary"
      dark
      prominent
      :height="$route.path === '/' ? '220' : '170' "
      src="mountains.png"
      fade-img-on-scroll
      scroll-threshold="500"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(55,236,186,.9), rgba(25,32,72,.9)"
        ></v-img>
      </template>
      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

          <v-spacer></v-spacer>
          <search-bar />
        </v-row>

        <v-row>
          <v-toolbar-title class="ml-2 text-h4">
            {{ $store.state.appTitle }}
          </v-toolbar-title>
        </v-row>

        <v-row>
          <date-time-bar />
        </v-row>

        <v-row
        v-if="$route.path === '/'"
        >
          <field-add-task />
        </v-row>
        
      </v-container>
    </v-app-bar>

    <v-main>
      <!--  -->
      <router-view> </router-view>
      <snack-bar />
    </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: "Todo", icon: "mdi-format-list-checks", to: "/" },
      { title: "About", icon: "mdi-help-box", to: "/about" },
    ],
  }),
  mounted() {
    this.$store.dispatch("getTasks");
  },
  components: {
    "snack-bar": require("@/components/Shared/SnackBar.vue").default,
    "search-bar": require("@/components/Tools/Search.vue").default,
    "date-time-bar": require("@/components/Tools/LiveDateTime.vue").default,
    "field-add-task": require("@/components/ToDo/AddTask.vue").default,
  },
};
</script>

<style lang="sass">
.header-container
  max-width: none !important
</style>