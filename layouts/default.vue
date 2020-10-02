<template>
    <v-app>
        <v-card color="dark" flat tile fixed top>
            <v-toolbar>
            <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title v-bind:text="page_title ? page_title : 'Home'"></v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn text to="/">Home</v-btn>
            <v-btn text to="/anggota">About</v-btn>
            <v-btn icon>
                <v-icon>mdi-brightness-3</v-icon>
            </v-btn>
            </v-toolbar>
        </v-card>
        <main>
            <v-container fluid>
                <Nuxt />
            </v-container>
        </main>
        <footer-kit></footer-kit>
        <v-navigation-drawer v-model="drawer" absolute bottom temporary>
            <v-list nav dense >
                <v-list-item-group
                v-model="group">
                    <v-list-item>
                    </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>
    </v-app>
</template>
<script>
export default {
    props: ['page_title'],
    data: () => ({
      drawer: false,
      group: null,
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
}
</script>