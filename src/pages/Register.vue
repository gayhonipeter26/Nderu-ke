<template>
  <div>
    <!-- Trigger button -->
    <button @click="openModal" class="open-btn">Register</button>

    <!-- Popup Modal -->
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>

        <h2>Create Your Account</h2>
        <form @submit.prevent="submitForm">
          <label>Full Name</label>
          <input type="text" v-model="form.name" required />

          <label>Email</label>
          <input type="email" v-model="form.email" required />

          <label>Password</label>
          <input type="password" v-model="form.password" required />

          <label>Confirm Password</label>
          <input type="password" v-model="form.confirmPassword" required />

          <label>Service Type</label>
          <select v-model="form.service" required>
            <option value="">-- Select --</option>
            <option value="pos">POS System</option>
            <option value="ecommerce">E-Commerce</option>
            <option value="portfolio">Portfolio Website</option>
          </select>

          <button type="submit" class="btn">Register</button>
        </form>

        <!-- Mock verification -->
        <div v-if="submitted" class="verify">
          <p>📧 Verification email sent to <strong>{{ form.email }}</strong>.</p>
          <button @click="verifyAccount" class="btn">Verify Now</button>
        </div>

        <div v-if="verified" class="success">
          <p>✅ Account verified! You can now log in.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showModal: false,
      form: {
        name: '',
        email: '',
        password: '',
        confirmPassword: '',
        service: ''
      },
      submitted: false,
      verified: false
    }
  },
  methods: {
    openModal() {
      this.showModal = true
    },
    closeModal() {
      this.showModal = false
      this.submitted = false
      this.verified = false
    },
    submitForm() {
      if (this.form.password !== this.form.confirmPassword) {
        alert("Passwords do not match!")
        return
      }
      this.submitted = true
    },
    verifyAccount() {
      this.verified = true
      this.submitted = false
    }
  }
}
</script>

<style scoped>
/* Modal Overlay */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
}

/* Modal Content */
.modal-content {
  background: #0a0a0a;
  padding: 2rem;
  border-radius: 12px;
  width: 90%;
  max-width: 500px;
  color: #fff;
  position: relative;
  animation: slideDown 0.3s ease;
}

/* Close Button */
.close {
  position: absolute;
  top: 12px;
  right: 16px;
  font-size: 1.5rem;
  color: #fff;
  cursor: pointer;
}

/* Open Button */
.open-btn {
  background: #00ff88;
  color: #0a0a0a;
  padding: 0.8rem 1.6rem;
  border-radius: 6px;
  border: none;
  cursor: pointer;
  font-weight: 600;
}

/* Animations */
@keyframes slideDown {
  from { transform: translateY(-20px); opacity: 0; }
  to { transform: translateY(0); opacity: 1; }
}
</style>
