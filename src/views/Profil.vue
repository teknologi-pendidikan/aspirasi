<template>
  <section id="settings">
    <div class="col1">
      <h3>Profil Anda</h3>

      <!-- <transition name="fade">
        <p v-if="showSuccess" class="success">profile updated</p>
      </transition> -->

      <form @submit.prevent>
        <label for="name">Nama</label>
        <input v-model.trim="name" type="text" :placeholder="userProfile.name" id="name" readonly/>

        <label for="title">Offering</label>
        <input v-model.trim="title" type="text" :placeholder="userProfile.title" id="title" readonly/>

        <!-- <button @click="updateProfile()" class="button">Update Profile</button> -->
      </form>
    </div>
  </section>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      name: '',
      title: '',
      showSuccess: false
    }
  },
  computed: {
    ...mapState(['userProfile'])
  },
  methods: {
    // updateProfile() {
    //   this.$store.dispatch('updateProfile', {
    //     name: this.name !== '' ? this.name : this.userProfile.name,
    //     title: this.title !== '' ? this.title : this.userProfile.title
    //   })

    //   this.name = ''
    //   this.title = ''

    //   this.showSuccess = true

    //   setTimeout(() => {
    //     this.showSuccess = false
    //   }, 2000)
    // }
  }
}
</script>
