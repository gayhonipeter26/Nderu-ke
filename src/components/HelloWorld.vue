<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <div class="hero-section">
    <div class="geometric-bg"></div>
    <div class="floating-orb"></div>
    
    <div class="hero-content">
      <h1>
        <span class="highlight">Own</span> {{ msg }}
      </h1>
      
      <div class="interactive-card">
        <div class="card-header">
          <h3>Interactive Counter</h3>
          <span class="status-indicator">Live</span>
        </div>
        <button type="button" @click="count++" class="count-button">
          <span class="count-value">{{ count }}</span>
          <span class="count-label">clicks</span>
        </button>
        <p class="card-description">
          Edit <code>components/HelloWorld.vue</code> to test HMR
        </p>
      </div>

      <div class="info-grid">
        <div class="info-card">
          <h4>Quick Start</h4>
          <p>
            Check out
            <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">
              create-vue
            </a>
            , the official Vue + Vite starter
          </p>
        </div>

        <div class="info-card">
          <h4>IDE Support</h4>
          <p>
            Learn more about IDE Support for Vue in the
            <a href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support" target="_blank">
              Vue Docs Scaling up Guide
            </a>
            .
          </p>
        </div>
      </div>

      <p class="read-the-docs">
        Click on the Vite and Vue logos to learn more
      </p>
    </div>

    <div class="floating-guide-card">
      <div class="guide-icon">📚</div>
      <h4>Vue Guide</h4>
      <p>Interactive Development</p>
      <button class="guide-button">GET STARTED →</button>
    </div>
  </div>
</template>

<style scoped>
.hero-section {
  background: #0a0a0a;
  color: white;
  min-height: 100vh;
  padding: 4rem 2rem;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Geometric Background Elements */
.geometric-bg {
  position: absolute;
  top: -20%;
  right: -10%;
  width: 60%;
  height: 120%;
  background: linear-gradient(135deg, rgba(0, 255, 136, 0.1) 0%, transparent 70%);
  transform: skewY(-15deg);
  z-index: 1;
}

.floating-orb {
  position: absolute;
  top: 20%;
  right: 15%;
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, rgba(255, 255, 255, 0.2) 30%, transparent 70%);
  border-radius: 50%;
  filter: blur(1px);
  z-index: 2;
  animation: float 6s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-20px); }
}

.hero-content {
  max-width: 1000px;
  position: relative;
  z-index: 3;
  text-align: center;
}

h1 {
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 300;
  line-height: 1.1;
  margin: 0 0 3rem;
  letter-spacing: -0.03em;
}

.highlight {
  color: #00ff88;
  font-weight: 700;
}

/* Interactive Card */
.interactive-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 16px;
  padding: 2rem;
  margin: 2rem auto;
  max-width: 400px;
  transition: all 0.3s ease;
}

.interactive-card:hover {
  transform: translateY(-5px);
  border-color: rgba(0, 255, 136, 0.3);
  box-shadow: 0 20px 40px rgba(0, 255, 136, 0.1);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.card-header h3 {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 600;
  color: white;
}

.status-indicator {
  background: #00ff88;
  color: #0a0a0a;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
}

.count-button {
  background: linear-gradient(135deg, #00ff88 0%, #00e079 100%);
  color: #0a0a0a;
  border: none;
  border-radius: 12px;
  padding: 1.5rem;
  width: 100%;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.count-button:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 25px rgba(0, 255, 136, 0.3);
}

.count-button:active {
  transform: scale(0.98);
}

.count-value {
  font-size: 2rem;
  font-weight: 700;
  line-height: 1;
}

.count-label {
  font-size: 0.9rem;
  opacity: 0.8;
}

.card-description {
  margin: 1.5rem 0 0;
  font-size: 0.9rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.5;
}

.card-description code {
  background: rgba(0, 255, 136, 0.1);
  color: #00ff88;
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  font-size: 0.85rem;
  border: 1px solid rgba(0, 255, 136, 0.2);
}

/* Info Grid */
.info-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  margin: 3rem 0;
}

.info-card {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 1.5rem;
  transition: all 0.3s ease;
  text-align: left;
}

.info-card:hover {
  border-color: rgba(0, 255, 136, 0.2);
  background: rgba(255, 255, 255, 0.05);
}

.info-card h4 {
  margin: 0 0 1rem;
  color: #00ff88;
  font-size: 1rem;
  font-weight: 600;
}

.info-card p {
  margin: 0;
  font-size: 0.9rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
}

.info-card a {
  color: #00ff88;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
}

.info-card a:hover {
  color: #00e079;
  text-decoration: none;
}

.info-card a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 1px;
  background: #00ff88;
  transition: width 0.3s ease;
}

.info-card a:hover::after {
  width: 100%;
}

/* Floating Guide Card */
.floating-guide-card {
  position: absolute;
  top: 25%;
  right: 5%;
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 12px;
  padding: 1.5rem;
  width: 200px;
  z-index: 4;
  text-align: center;
  animation: float 8s ease-in-out infinite;
}

.guide-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.floating-guide-card h4 {
  margin: 0 0 0.5rem;
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
}

/* Read the docs */
.read-the-docs {
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.9rem;
  margin-top: 3rem;
  font-style: italic;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-section {
    padding: 2rem 1rem;
  }
  
  .floating-guide-card,
  .floating-orb {
    display: none;
  }
  
  .info-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  .info-card {
    text-align: center;
  }
  
  .interactive-card {
    max-width: 100%;
  }
}

/* Smooth animations */
* {
  transition: all 0.3s ease;
}

/* Selection styling */
::selection {
  background: #00ff88;
  color: #0a0a0a;
}
</style>