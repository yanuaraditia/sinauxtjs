<template>
    <v-footer
    color="dark"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
      <v-btn
        v-for="link in links"
        :key="link.key"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link.key }}
      </v-btn>
      <v-col
        class="dark py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-row>
  </v-footer>
</template>
<script>
export default {
  data() {
    return {
      links: [
        {
          key: 'Home',
          slug: '/about'
        }
      ]
    }
  }
}
</script>