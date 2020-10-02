<template>
    <v-app>
        <v-card color="dark" flat tile fixed top>
            <v-toolbar flat>
                <v-toolbar-title v-bind:text="page_title ? page_title : 'Home'"></v-toolbar-title>
                <v-spacer></v-spacer>
                <v-btn text to="/">Home</v-btn>
                <v-btn text to="/anggota">People</v-btn>
                <v-btn icon>
                    <v-icon>mdi-brightness-3</v-icon>
                </v-btn>
            </v-toolbar>
        </v-card>
        <main>
            <v-container fluid class="py-md-5 my-3 my-md-7">
                <Nuxt />
            </v-container>
        </main>
        <footer-kit></footer-kit>
    </v-app>
</template>
<script>
export default {
    props: ['page_title'],
}
</script>