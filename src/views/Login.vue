<template>
  <div id="login">
    <PasswordReset v-if="showPasswordReset" @close="togglePasswordReset()"></PasswordReset>
    <section>
      <div class="col1">
        <h1>SUARA - HMJ TEP UM</h1>
        <p>Selamat datang di aplikasi <b>SUARA</b>. SUARA adalah aplikasi pelaporan dan penyampaian aspirasi mahasiswa. Aplikasi ini di-update secara realtime dan dapat diakses oleh seluruh sivitas akademik jurusan TEP UM. </p>
      </div>
      <div :class="{ 'signup-form': !showLoginForm }" class="col2">
        <form v-if="showLoginForm" @submit.prevent>
          <h1>Selamat Datang</h1>
          <div>
            <label for="email1">Email</label>
            <input v-model.trim="loginForm.email" type="text" placeholder="username@students.um.ac.id" id="email1" />
          </div>
          <div>
            <label for="password1">Password</label>
            <input v-model.trim="loginForm.password" type="password" placeholder="******" id="password1" />
          </div>
          <button @click="login()" class="button">Log In</button>
          <div class="extras">
            <a @click="togglePasswordReset()">Lupa Kata Sandi</a>
            <a @click="toggleForm()">Buat Akun</a>
            <a @click="loginAnomymous()">Login Anonimus</a>
          </div>
        </form>
        <form v-else @submit.prevent>
          <h1>Registrasi</h1>
          <div>
            <label for="name">Nama</label>
            <input v-model.trim="signupForm.name" type="text" placeholder="Mas Dadang" id="name" />
          </div>
          <div>
            <label for="title">Offering</label>
            <input v-model.trim="signupForm.title" type="text" placeholder="A2Z" id="title" />
          </div>
          <div>
            <label for="email2">Email</label>
            <input v-model.trim="signupForm.email" type="text" placeholder="@students.um.ac.id" id="email2" />
          </div>
          <div>
            <label for="password2">Kata Sandi</label>
            <input v-model.trim="signupForm.password" type="password" placeholder="Minimal 6 Karakter " id="password2" />
          </div>
          <button @click="signup()" class="button">Daftar Akun</button>
          <div class="extras">
            <a @click="toggleForm()">Kembali ke Laman Login</a>
          </div>
        </form>
      </div>
    </section>
  </div>
</template>

<script>
import PasswordReset from '@/components/PasswordReset'

export default {
  components: {
    PasswordReset
  },
  data() {
    return {
      loginForm: {
        email: '',
        password: ''
      },
      signupForm: {
        name: '',
        title: '',
        email: '',
        password: ''
      },
      showLoginForm: true,
      showPasswordReset: false
    }
  },
  methods: {
    toggleForm() {
      this.showLoginForm = !this.showLoginForm
    },
    togglePasswordReset() {
      this.showPasswordReset = !this.showPasswordReset
    },
    login() {
      this.$store.dispatch('login', {
        email: this.loginForm.email,
        password: this.loginForm.password
      })
    },
    loginAnomymous() {
      this.$store.dispatch('login', {
        email: 'anomymous@reng.my.id',
        password: 'logintamu'
      })
    },
    signup() {
      this.$store.dispatch('signup', {
        email: this.signupForm.email,
        password: this.signupForm.password,
        name: this.signupForm.name,
        title: this.signupForm.title
      })
    }
  }
}
</script>
