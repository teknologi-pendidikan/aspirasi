<template>
  <header>
    <section>
      <div class="col1">
        <router-link to="/">
          <h3>KINERJA - HMJ TEP</h3>
        </router-link>
        <ul class="inline">
          <li>
            <router-link to="/">Beranda</router-link>
          </li>
          <li>
            <router-link to="/profil">Profil</router-link>
          </li>
          <li><a @click="logout()">logout</a></li>
        </ul>
      </div>
    </section>
  </header>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$store.dispatch('logout')
    }
  }
}
</script>
