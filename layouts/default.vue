<template>
    <v-app class="overflow-auto">
        <div
        >
            <v-system-bar fixed app color="amber darken-3"></v-system-bar>
            <v-app-bar
            color="amber accent-4"
            dark
            fixed app
            >
            <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

            <v-toolbar-title>My files</v-toolbar-title>

            <v-spacer></v-spacer>

            <v-btn icon>
                <v-icon>mdi-magnify</v-icon>
            </v-btn>

            <v-btn icon to="/anggota">
                <v-icon>mdi-account-supervisor</v-icon>
            </v-btn>

            <v-btn icon>
                <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
            </v-app-bar>

            <v-navigation-drawer
            absolute
            bottom
            temporary
            v-model="drawer">
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
                <v-list-item
                v-for="item in items"
                :key="item.title"
                :to="'/'"
                link
                class="transparent"
                elevation="0"
                >
                <v-list-item-icon>
                    <v-icon>{{ item.icon }}</v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
                </v-list-item>
            </v-list>
            </v-navigation-drawer>
            <main style="margin-top: 90px">
                <v-container fluid class="py-md-5 my-3 my-md-7">
                    <Nuxt />
                </v-container>
            </main>
            <footer-kit></footer-kit>
        </div>
    </v-app>
</template>
<script>
export default {
    props: ['page_title'],
        data: () => ({
      drawer: false,
      group: null,
              items: [
          { title: 'Dashboard', icon: 'mdi-view-dashboard' },
          { title: 'Photos', icon: 'mdi-image' },
          { title: 'About', icon: 'mdi-help-box' },
        ],
        right: null,
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
}
</script>