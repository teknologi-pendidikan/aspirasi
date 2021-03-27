<template>
  <div class="modal">
    <div class="modal-content">
      <div @click="$emit('close')" class="close">Tutup</div>
      <h3>Reset Kata Sandi</h3>
      <div v-if="!showSuccess">
        <p>Masukkan email anda untuk mereset kata sandi</p>
        <form @submit.prevent>
          <input v-model.trim="email" type="email" placeholder="username@students.um.ac.id" />
        </form>
        <p v-if="errorMsg !== ''" class="error">{{ errorMsg }}</p>
        <button @click="resetPassword()" class="button">Reset Kata sandi</button>
      </div>
      <p v-else>Cek email anda untuk mereset kata sandi.</p>
    </div>
  </div>
</template>

<script>
import { auth } from '@/firebase'

export default {
  data() {
    return {
      email: '',
      showSuccess: false,
      errorMsg: ''
    }
  },
  methods: {
    async resetPassword() {
      this.errorMsg = ''

      try {
        await auth.sendPasswordResetEmail(this.email)
        this.showSuccess = true
      } catch (err) {
        this.errorMsg = err.message
      }
    }
  }
}
</script>
