<template>
  <header class="modern-header">
    <div class="header-content">
      <div class="logo-section">
        <h1 class="logo">
          <span class="logo-main">Nderu.ke</span>
          <span class="logo-suffix">Ent</span>
        </h1>
      </div>
      
  <nav class="main-nav">
  <a href="#home" class="nav-link">
    <span>Home</span>
  </a>
  <a href="#services" class="nav-link">
    <span>Services</span>
  </a>
  <a href="#how-it-works" class="nav-link">
    <span>How it works</span>
  </a>
  <a href="#pricing" class="nav-link">
    <span>Pricing</span>
  </a>
  <a href="#faq" class="nav-link">
    <span>FAQ</span>
  </a>
</nav>

      <div class="header-actions">
        <button class="contact-btn">
          <span>Get in touch</span>
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
            <path d="M6 12L10 8L6 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
      </div>
    </div>
    
    <!-- Mobile Menu Button -->
    <div class="mobile-menu-btn" @click="toggleMobileMenu">
      <span></span>
      <span></span>
      <span></span>
    </div>
    
    <!-- Mobile Menu Overlay -->
    <div class="mobile-menu" :class="{ active: mobileMenuOpen }">
      <div class="mobile-menu-content">
        <nav class="mobile-nav">
          <a href="#services" class="mobile-nav-link" @click="closeMobileMenu">
            Services
          </a>
          <a href="#how-it-works" class="mobile-nav-link" @click="closeMobileMenu">
            How it works
          </a>
          <a href="#pricing" class="mobile-nav-link" @click="closeMobileMenu">
            Pricing
          </a>
          <a href="#faq" class="mobile-nav-link" @click="closeMobileMenu">
            FAQ
          </a>
        </nav>
        <button class="mobile-contact-btn" @click="closeMobileMenu">
          Get in touch
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

const closeMobileMenu = () => {
  mobileMenuOpen.value = false
}
</script>

<style scoped>
.modern-header {
  background: rgba(10, 10, 10, 0.95);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  transition: all 0.3s ease;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1400px;
  margin: 0 auto;
  padding: 1.25rem 2rem;
}

/* Logo Section */
.logo-section {
  display: flex;
  align-items: center;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0;
  color: white;
  letter-spacing: -0.02em;
  display: flex;
  align-items: baseline;
  gap: 0.25rem;
}

.logo-main {
  color: #00ff88;
  position: relative;
}

.logo-main::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, #00ff88 0%, transparent 100%);
  opacity: 0.6;
}

.logo-suffix {
  color: rgba(255, 255, 255, 0.8);
  font-weight: 300;
  font-size: 1.2rem;
}

/* Main Navigation */
.main-nav {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-link {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  position: relative;
  padding: 0.5rem 0;
  transition: all 0.3s ease;
  overflow: hidden;
}

.nav-link span {
  position: relative;
  z-index: 1;
  transition: all 0.3s ease;
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: radial-gradient(circle, rgba(0, 255, 136, 0.1) 0%, transparent 70%);
  transform: translate(-50%, -50%);
  transition: all 0.4s ease;
  border-radius: 50%;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, #00ff88 0%, #00e079 100%);
  transition: all 0.3s ease;
}

.nav-link:hover {
  color: #00ff88;
}

.nav-link:hover::before {
  width: 120%;
  height: 120%;
}

.nav-link:hover::after {
  width: 100%;
}

.nav-link:hover span {
  transform: translateY(-1px);
}

/* Header Actions */
.header-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.contact-btn {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.2);
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  position: relative;
  overflow: hidden;
}

.contact-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent 0%, rgba(0, 255, 136, 0.1) 50%, transparent 100%);
  transition: all 0.6s ease;
}

.contact-btn:hover {
  color: #00ff88;
  border-color: #00ff88;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 255, 136, 0.15);
}

.contact-btn:hover::before {
  left: 100%;
}

.contact-btn svg {
  transition: all 0.3s ease;
}

.contact-btn:hover svg {
  transform: translateX(2px);
}

/* Mobile Menu Button */
.mobile-menu-btn {
  display: none;
  flex-direction: column;
  cursor: pointer;
  padding: 0.5rem;
  gap: 4px;
}

.mobile-menu-btn span {
  width: 20px;
  height: 2px;
  background: white;
  transition: all 0.3s ease;
  border-radius: 1px;
}

.mobile-menu-btn:hover span {
  background: #00ff88;
}

/* Mobile Menu */
.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(10, 10, 10, 0.98);
  backdrop-filter: blur(20px);
  transform: translateX(-100%);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 999;
}

.mobile-menu.active {
  transform: translateX(0);
}

.mobile-menu-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
  padding: 2rem;
  text-align: center;
}

.mobile-nav {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  margin-bottom: 3rem;
}

.mobile-nav-link {
  color: white;
  text-decoration: none;
  font-size: 1.5rem;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
}

.mobile-nav-link:hover {
  color: #00ff88;
  transform: translateX(10px);
}

.mobile-contact-btn {
  background: #00ff88;
  color: #0a0a0a;
  border: none;
  padding: 1rem 2rem;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.mobile-contact-btn:hover {
  background: #00e079;
  transform: translateY(-2px);
}

/* Responsive Design */
@media (max-width: 768px) {
  .header-content {
    padding: 1rem 1.5rem;
  }
  
  .main-nav,
  .header-actions {
    display: none;
  }
  
  .mobile-menu-btn {
    display: flex;
  }
  
  .logo {
    font-size: 1.3rem;
  }
}

@media (max-width: 480px) {
  .header-content {
    padding: 1rem;
  }
  
  .logo {
    font-size: 1.2rem;
  }
}

/* Scroll Effect */
.modern-header.scrolled {
  background: rgba(10, 10, 10, 0.98);
  border-bottom-color: rgba(255, 255, 255, 0.15);
}

/* Smooth scrolling for anchor links */
html {
  scroll-behavior: smooth;
}

/* Selection styling */
::selection {
  background: #00ff88;
  color: #0a0a0a;
}
</style>