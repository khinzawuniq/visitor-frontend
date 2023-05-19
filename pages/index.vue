<template>
  <div class="welcome-page">
    <b-container class="welcome-content">
      <h1>Welcome to My Visitor Website</h1>
      <p>Thank you for visiting our website. We provide high-quality services for all your needs.</p>
      <b-button variant="primary" @click="goToRegisterPage">
        <i class="fas fa-user"></i>
        Register
      </b-button>
    </b-container>
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css';
export default {
  name: 'WelcomePage',
  methods: {
    goToRegisterPage() {
      // Redirect to the register page
      window.location.href = '/register';
    }
  }
}
</script>

<style scoped>
.welcome-page {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.welcome-content {
  text-align: center;
}

.welcome-content h1 {
  font-size: 41px;
  margin-bottom: 20px;
  font-weight: bold;
}

.welcome-content p {
  font-size: 23px;
  margin-bottom: 30px;
}

.welcome-content b-button,button.btn.btn-primary {
  font-size: 18px;
}
</style>
