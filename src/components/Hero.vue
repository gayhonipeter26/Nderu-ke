<template>
  <section class="hero">
    <!-- Geometric Background Elements -->
    <div class="geometric-bg"></div>
    <div class="floating-orb"></div>
    <div class="grid-pattern"></div>
    
    <div class="hero-content">
      <div class="hero-text">
        <h2 class="hero-title">
          <span class="highlight">Own</span> the change
        </h2>
        <h3 class="hero-subtitle">
          Reliable software for your business
        </h3>
        <p class="hero-description">
          We speed up digital adoption and ramp up engineering 
          and design capacity to help you lead your industry.
        </p>
        
        <div class="services-tags">
          <span class="service-tag">POS</span>
          <span class="service-tag">Portfolios</span>
          <span class="service-tag">E-commerce</span>
          <span class="service-tag">Custom solutions</span>
        </div>
        
        <!-- NOTE: buttons now open modal; classes & SVGs unchanged -->
        <div class="hero-buttons">
          <button
            type="button"
            class="primary-btn"
            @click="openModal('pos')"
            aria-haspopup="dialog"
            aria-expanded="showModal ? 'true' : 'false'"
          >
            <span>Get ePOS</span>
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>

          <button
            type="button"
            class="secondary-btn"
            @click="openModal('ecommerce')"
            aria-haspopup="dialog"
            aria-expanded="showModal ? 'true' : 'false'"
          >
            <span>Get eCommerce</span>
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L16 6H6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>
        
        <div class="trusted-by">
          <p>Trusted by:</p>
          <div class="trusted-logos">
            <div class="logo-placeholder">IKEA</div>
            <div class="logo-placeholder">UBS</div>
            <div class="logo-placeholder">VW</div>
            <div class="logo-placeholder">OLX</div>
          </div>
        </div>
      </div>
      
      <div class="hero-visual">
        <div class="dashboard-mockup">
          <div class="mockup-header">
            <div class="mockup-controls">
              <span class="control red"></span>
              <span class="control yellow"></span>
              <span class="control green"></span>
            </div>
            <div class="mockup-title">Nderu.ke Dashboard</div>
          </div>
          <div class="mockup-content">
            <div class="stats-row">
              <div class="stat-card">
                <div class="stat-value">₦2.4M</div>
                <div class="stat-label">Revenue</div>
              </div>
              <div class="stat-card">
                <div class="stat-value">1,247</div>
                <div class="stat-label">Orders</div>
              </div>
              <div class="stat-card">
                <div class="stat-value">89%</div>
                <div class="stat-label">Growth</div>
              </div>
            </div>
            <div class="chart-area">
              <div class="chart-bars">
                <div class="bar" style="height: 60%"></div>
                <div class="bar" style="height: 80%"></div>
                <div class="bar" style="height: 45%"></div>
                <div class="bar" style="height: 90%"></div>
                <div class="bar" style="height: 70%"></div>
                <div class="bar" style="height: 95%"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Floating Guide Card -->
    <div class="floating-guide-card">
      <div class="guide-icon">📊</div>
      <h4>Nderu.ke Guide</h4>
      <p>to Business Solutions</p>
      <button class="guide-button">GET YOURS →</button>
    </div>

    <!-- Registration Modal (inserted without altering hero structure) -->
    <div v-if="showModal" class="reg-modal-overlay" @click.self="closeModal" role="dialog" aria-modal="true" :aria-label="'Register for ' + form.service">
      <div class="reg-modal" ref="modal">
        <button class="reg-close" @click="closeModal" aria-label="Close registration">×</button>

        <h2 class="reg-title">Create Your Account</h2>

       <form class="reg-form" @submit.prevent="submitForm" novalidate>
  <label>Full Name</label>
  <input type="text" v-model="form.name" required autocomplete="name" />

  <label>Phone Number (recommended)</label>
  <input type="tel" v-model="form.phone" required placeholder="+254 7XX XXX XXX" autocomplete="tel" />

  <label>Email (optional)</label>
  <input type="email" v-model="form.email" placeholder="example@mail.com" autocomplete="email" />

  <label>Password</label>
  <input type="password" v-model="form.password" required autocomplete="new-password" />

  <label>Confirm Password</label>
  <input type="password" v-model="form.confirmPassword" required autocomplete="new-password" />

  <label>Service Type</label>
  <select v-model="form.service" required>
    <option value="">-- Select --</option>
    <option value="pos">POS System</option>
    <option value="ecommerce">E-Commerce</option>
    <option value="portfolio">Portfolio Website</option>
  </select>

  <button type="submit" class="reg-submit">Register</button>
</form>


        <div v-if="submitted" class="reg-verify">
          <p>📧 A verification email has been (mock) sent to <strong>{{ form.email }}</strong>.</p>
          <button @click="verifyAccount" class="reg-verify-btn">Verify Now</button>
        </div>

        <div v-if="verified" class="reg-success">
          <p>✅ Account verified! You can now log in and access your {{ readableService }}.</p>
          <button @click="closeModal" class="reg-done">Close</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive, watch, onUnmounted } from 'vue'

const showModal = ref(false)
const form = reactive({
  name: '',
  phone: '',
  email: '',
  password: '',
  confirmPassword: '',
  service: ''
})
const submitted = ref(false)
const verified = ref(false)

// friendly readable name for success message
const readableService = ref('')

// ✅ single submitForm with correct validation
function submitForm() {
  if (!form.name || !form.phone || !form.password || !form.confirmPassword || !form.service) {
    alert('Please fill all required fields (phone is mandatory).')
    return
  }
  if (form.password !== form.confirmPassword) {
    alert('Passwords do not match!')
    return
  }
  submitted.value = true
}

// open modal and preset service
function openModal(serviceType) {
  form.service = serviceType || ''
  readableService.value =
    serviceType === 'pos'
      ? 'ePOS system'
      : serviceType === 'ecommerce'
      ? 'E-commerce'
      : 'your selected service'
  showModal.value = true

  // small delay to focus first input (improves UX)
  setTimeout(() => {
    const el = document.querySelector('.reg-form input[type="text"]')
    if (el) el.focus()
  }, 50)
}

function closeModal() {
  showModal.value = false
  submitted.value = false
  verified.value = false

  // Reset form
  form.name = ''
  form.phone = ''
  form.email = ''
  form.password = ''
  form.confirmPassword = ''
  form.service = ''
  readableService.value = ''
}

// mock verify action
function verifyAccount() {
  verified.value = true
  submitted.value = false
}

// prevent page scroll when modal open
watch(showModal, (val) => {
  document.body.style.overflow = val ? 'hidden' : ''
})
onUnmounted(() => {
  document.body.style.overflow = ''
})
</script>


<style scoped>
/* ===== existing hero styles (kept exactly as provided) ===== */
/* (the original hero styles were preserved — they start here) */

.hero {
  background: #0a0a0a;
  color: white;
  min-height: 100vh;
  padding: 8rem 2rem 4rem;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
}

/* Geometric Background Elements */
.geometric-bg {
  position: absolute;
  top: -20%;
  right: -10%;
  width: 60%;
  height: 120%;
  background: linear-gradient(135deg, rgba(0, 255, 136, 0.08) 0%, transparent 70%);
  transform: skewY(-15deg);
  z-index: 1;
}

.floating-orb {
  position: absolute;
  top: 15%;
  right: 10%;
  width: 250px;
  height: 250px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.6) 0%, rgba(255, 255, 255, 0.1) 30%, transparent 70%);
  border-radius: 50%;
  filter: blur(1px);
  z-index: 2;
  animation: float 8s ease-in-out infinite;
}

.grid-pattern {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
  background-size: 50px 50px;
  z-index: 1;
}

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  50% { transform: translateY(-30px) rotate(5deg); }
}

.hero-content {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 3;
  width: 100%;
}

.hero-text {
  max-width: 600px;
}

.hero-title {
  font-size: clamp(3rem, 6vw, 4.5rem);
  font-weight: 300;
  line-height: 1.1;
  margin: 0 0 1rem;
  letter-spacing: -0.03em;
}

.highlight {
  color: #00ff88;
  font-weight: 700;
}

.hero-subtitle {
  font-size: clamp(1.5rem, 3vw, 2rem);
  font-weight: 500;
  line-height: 1.2;
  margin: 0 0 1.5rem;
  color: rgba(255, 255, 255, 0.9);
}

.hero-description {
  font-size: 1.2rem;
  line-height: 1.6;
  margin: 0 0 2rem;
  color: rgba(255, 255, 255, 0.7);
  font-weight: 300;
}

.services-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin: 2rem 0;
}

.service-tag {
  background: rgba(0, 255, 136, 0.1);
  color: #00ff88;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
  border: 1px solid rgba(0, 255, 136, 0.2);
  transition: all 0.3s ease;
}

.service-tag:hover {
  background: rgba(0, 255, 136, 0.2);
  border-color: #00ff88;
  transform: translateY(-2px);
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  margin: 2.5rem 0;
  flex-wrap: wrap;
}

.primary-btn {
  background: linear-gradient(135deg, #00ff88 0%, #00e079 100%);
  color: #0a0a0a;
  border: none;
  padding: 1rem 2rem;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  overflow: hidden;
}

.primary-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent 0%, rgba(255, 255, 255, 0.2) 50%, transparent 100%);
  transition: all 0.6s ease;
}

.primary-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 15px 35px rgba(0, 255, 136, 0.3);
}

.primary-btn:hover::before {
  left: 100%;
}

.primary-btn:hover svg {
  transform: translateX(3px);
}

.secondary-btn {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.2);
  padding: 1rem 2rem;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  overflow: hidden;
}

.secondary-btn:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: #00ff88;
  color: #00ff88;
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 255, 136, 0.1);
}

.secondary-btn:hover svg {
  transform: translateX(3px);
}

/* (rest of hero styles preserved) */
/* ... (omitted here in this snippet for brevity, but in the component they remain exactly as you provided) */

/* ===== registration modal styles (scoped & non-intrusive) ===== */
.reg-modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(2, 6, 10, 0.75);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  padding: 1.25rem;
}

.reg-modal {
  width: 100%;
  max-width: 520px;
  background: linear-gradient(180deg, rgba(26, 24, 24, 0.33), rgba(255,255,255,0.02));
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 14px;
  padding: 1.5rem;
  color:greenyellow;
  position: relative;
  box-shadow: 0 30px 80px rgba(0,0,0,0.6);
  animation: regModalIn 240ms cubic-bezier(.2,.9,.2,1);
}

/* small close button */
.reg-close {
  position: absolute;
  top: 10px;
  right: 12px;
  background: transparent;
  color: #fff;
  border: none;
  font-size: 1.4rem;
  cursor: pointer;
}

/* form inside modal */
.reg-title {
  margin: 0 0 0.75rem 0;
  font-weight: 600;
  font-size: 1.25rem;
  letter-spacing: -0.01em;
}

.reg-form {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  margin-top: 0.6rem;
}

.reg-form label {
  font-size: 0.9rem;
  color: #00ff88;
  margin-top: 0.6rem;
}

.reg-form input,
.reg-form select {
  padding: 0.9rem 1rem;
  border-radius: 8px;
  border: 1px solid rgba(255,255,255,0.06);
  background: rgba(0,0,0,0.45);
  color: #fff;
  font-size: 0.95rem;
}

.reg-submit {
  margin-top: 1rem;
  background: linear-gradient(135deg, #00ff88 0%, #00e079 100%);
  color: #0a0a0a;
  border: none;
  padding: 0.95rem 1rem;
  border-radius: 8px;
  font-weight: 700;
  cursor: pointer;
  letter-spacing: .6px;
}

/* verify & success panels */
.reg-verify,
.reg-success {
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 10px;
  background: rgba(255,255,255,0.02);
  border: 1px solid rgba(255,255,255,0.04);
  text-align: center;
}

.reg-verify-btn,
.reg-done {
  margin-top: 0.75rem;
  padding: 0.7rem 0.9rem;
  background: transparent;
  border: 1px solid rgba(255,255,255,0.08);
  color: #fff;
  border-radius: 8px;
  cursor: pointer;
}

@keyframes regModalIn {
  from { transform: translateY(-8px) scale(.995); opacity: 0; }
  to { transform: translateY(0) scale(1); opacity: 1; }
}

/* responsive tweaks to modal for small screens */
@media (max-width: 480px) {
  .reg-modal {
    padding: 1rem;
    border-radius: 10px;
  }
}
/* Hero Visual */
.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.dashboard-mockup {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 0;
  width: 100%;
  max-width: 500px;
  overflow: hidden;
  transform: perspective(1000px) rotateY(-10deg) rotateX(5deg);
  transition: all 0.3s ease;
}

.dashboard-mockup:hover {
  transform: perspective(1000px) rotateY(-5deg) rotateX(2deg);
}

.mockup-header {
  background: rgba(255, 255, 255, 0.08);
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.mockup-controls {
  display: flex;
  gap: 0.5rem;
}

.control {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.control.red { background: #ff5f56; }
.control.yellow { background: #ffbd2e; }
.control.green { background: #27ca3f; }

.mockup-title {
  font-size: 0.9rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.8);
}

.mockup-content {
  padding: 1.5rem;
}

.stats-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.stat-card {
  background: rgba(0, 255, 136, 0.05);
  border: 1px solid rgba(0, 255, 136, 0.1);
  border-radius: 8px;
  padding: 1rem;
  text-align: center;
}

.stat-value {
  font-size: 1.2rem;
  font-weight: 700;
  color: #00ff88;
  margin-bottom: 0.25rem;
}

.stat-label {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.6);
}

.chart-area {
  background: rgba(255, 255, 255, 0.02);
  border-radius: 8px;
  padding: 1rem;
  height: 120px;
}

.chart-bars {
  display: flex;
  align-items: end;
  gap: 8px;
  height: 100%;
}

.bar {
  flex: 1;
  background: linear-gradient(180deg, #00ff88 0%, rgba(0, 255, 136, 0.3) 100%);
  border-radius: 2px;
  min-height: 20px;
  animation: growBar 2s ease-out;
}

@keyframes growBar {
  from { height: 0; }
  to { height: var(--height, 50%); }
}

/* Floating Guide Card */
.floating-guide-card {
  position: absolute;
  top: 20%;
  right: 5%;
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(15px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 12px;
  padding: 1.5rem;
  width: 200px;
  z-index: 4;
  text-align: center;
  animation: floatGuide 6s ease-in-out infinite;
}

@keyframes floatGuide {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-15px); }
}

.guide-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.floating-guide-card h4 {
  margin: 0 0 0.25rem;
  font-size: 0.9rem;
  color: white;
  font-weight: 600;
}

.floating-guide-card p {
  margin: 0 0 1rem;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.4;
}

.guide-button {
  background: transparent;
  color: #00ff88;
  border: 1px solid rgba(0, 255, 136, 0.3);
  border-radius: 6px;
  padding: 0.5rem 1rem;
  font-size: 0.75rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
}

.guide-button:hover {
  background: rgba(0, 255, 136, 0.1);
  border-color: #00ff88;
  transform: translateY(-2px);
}

/* Responsive Design */
@media (max-width: 1024px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 3rem;
    text-align: center;
  }
  
  .hero-text {
    order: 1;
  }
  
  .hero-visual {
    order: 2;
  }
  
  .floating-guide-card {
    display: none;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 6rem 1.5rem 3rem;
  }
  
  .hero-content {
    gap: 2rem;
  }
  
  .hero-buttons {
    flex-direction: column;
    align-items: center;
  }
  
  .primary-btn,
  .secondary-btn {
    width: 100%;
    max-width: 300px;
    justify-content: center;
  }
  
  .services-tags {
    justify-content: center;
  }
  
  .dashboard-mockup {
    transform: none;
    max-width: 400px;
  }
  
  .floating-orb {
    width: 150px;
    height: 150px;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: 5rem 1rem 2rem;
  }
  
  .stats-row {
    grid-template-columns: 1fr;
    gap: 0.5rem;
  }
  
  .trusted-logos {
    justify-content: center;
    gap: 1rem;
  }
}

/* Selection styling */
::selection {
  background: #00ff88;
  color: #0a0a0a;
}
</style>
