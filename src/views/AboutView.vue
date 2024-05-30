<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button @click="gotoDestination('/')"> goto home</button>
    <p>berapa id nya: {{ id }}</p>
    <p>berapa angka dari store: {{ angkaDariStore }}</p>
    <input type="number" v-model="angkaChildren">
    <button @click="sendToStore">kirim ke store</button>
  </div>
</template>

<script>
export default {
  name: 'AboutView',
  data() {
    return {
      angkaChildren: 0
    }
  },
  methods: {
    gotoDestination(params) {
      this.$router.push(params)
    },
    sendToStore() {
      this.$store.dispatch('about/changeAngkaValue', this.angkaChildren)
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    },
    angkaDariStore() {
      return this.$store.state.about.angka
    }
  }
}
</script>
