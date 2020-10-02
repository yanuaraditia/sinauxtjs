<template>
<v-card
    class="mx-auto text-center transparent"
    elevation=0
    max-width="434"
    tile
  >
      <v-row
        align="end"
        class="fill-height"
      >
        <v-col
          align-self="start"
          class="pa-0"
          cols="12"
        >
          <v-avatar
            class="profile"
            color="grey"
            size="164"
            tile
          >
            <v-img src="https://cdn.vuetifyjs.com/images/profiles/marcus.jpg"></v-img>
          </v-avatar>
        </v-col>
        <v-col class="py-0">
          <v-list-item
            color="rgba(0, 0, 0, .4)"
            dark
          >
            <v-list-item-content>
              <v-list-item-title class="title">
                Marcus Obrien
              </v-list-item-title>
              <v-list-item-subtitle>Network Engineer</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-col>
      </v-row>
  </v-card>
</template>
<script>
import axios from 'axios'
export default {
  validate({ params }) {
      this.params = params.id
    // Must be a number
    return /^\d+$/.test(params.id)
  },
  data() {
      return {
          anggota: null,
          isLoaded: false,
          title: 'Detail anggota'
      }
  },
  methods: {
      async getUser() {
          const id = this.$route.params.id
          await axios.get(`https://dev.imaka.or.id/api/anggota/${id}`)
          .then(res => {
              this.anggota = res.data.data
              this.title    = res.data.data.name
          })
      }
  },
  head() {
      return {
          title: this.title
      }
  },
  mounted() {
      this.getUser()
  }
}
</script>