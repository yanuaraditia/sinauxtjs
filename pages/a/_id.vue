<template>
    <h1>Testing</h1>
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