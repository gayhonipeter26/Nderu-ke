<template>
  <div class="home">
    <h1>Welcome to Nderu.ke Ent</h1>
    <p>We provide software services: POS, Personal Portfolios, Business Portfolios, E-commerce, and more.</p>
    
    <a href="/register" class="btn">Register Now</a>
  </div>
</template>

<style scoop>
/* Home Section Styling */
.home {
  background: #0a0a0a;
  color: white;
  text-align: center;
  padding: 12rem 3rem 8rem;
  margin-top: 80px;
  position: relative;
  overflow: hidden;
  min-height: 80vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* Geometric Background Elements */
.home::before {
  content: '';
  position: absolute;
  top: -20%;
  right: -10%;
  width: 60%;
  height: 120%;
  background: linear-gradient(135deg, rgba(0, 255, 136, 0.1) 0%, transparent 70%);
  transform: skewY(-15deg);
  z-index: 1;
}

.home::after {
  content: '';
  position: absolute;
  top: 20%;
  left: 5%;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, rgba(255, 255, 255, 0.2) 30%, transparent 70%);
  border-radius: 50%;
  filter: blur(1px);
  z-index: 2;
}

.home h1 {
  font-size: clamp(3rem, 8vw, 6rem);
  font-weight: 300;
  line-height: 1.1;
  margin: 0 0 2rem;
  letter-spacing: -0.03em;
  position: relative;
  z-index: 3;
  background: linear-gradient(135deg, #ffffff 0%, rgba(255, 255, 255, 0.8) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-align: center;
}

.home h1::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 3px;
  background: linear-gradient(90deg, transparent, #00ff88, transparent);
  border-radius: 2px;
}

/* Highlight company name */
.home h1 span,
.home h1 .highlight {
  color: #00ff88;
  font-weight: 700;
  -webkit-text-fill-color: #00ff88;
}

.home p {
  font-size: 1.25rem;
  line-height: 1.6;
  margin: 2rem auto 3rem;
  max-width: 700px;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 300;
  position: relative;
  z-index: 3;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 2rem;
  transition: all 0.3s ease;
}

.home p:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-2px);
  color: rgba(255, 255, 255, 0.95);
}

.home .btn {
  background: #00ff88;
  color: #0a0a0a;
  padding: 1.2rem 3rem;
  border: 2px solid #00ff88;
  border-radius: 8px;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 600;
  transition: all 0.3s ease;
  position: relative;
  z-index: 3;
  display: inline-block;
  overflow: hidden;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  box-shadow: 0 4px 20px rgba(0, 255, 136, 0.3);
}

.home .btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.6s ease;
}

.home .btn:hover {
  background: #00e079;
  color: #0a0a0a;
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 6px 25px rgba(0, 255, 136, 0.4);
}

.home .btn:hover::before {
  left: 100%;
}

.home .btn:active {
  transform: translateY(-1px) scale(1.02);
}

/* Add floating elements */
.home .floating-element {
  position: absolute;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  z-index: 1;
  animation: float 8s ease-in-out infinite;
}

.home .floating-element:nth-child(1) {
  width: 80px;
  height: 80px;
  top: 15%;
  left: 10%;
  animation-delay: -2s;
}

.home .floating-element:nth-child(2) {
  width: 60px;
  height: 60px;
  top: 60%;
  right: 15%;
  animation-delay: -4s;
}

@keyframes float {
  0%, 100% { transform: translateY(0px) rotate(0deg); }
  25% { transform: translateY(-20px) rotate(90deg); }
  50% { transform: translateY(-10px) rotate(180deg); }
  75% { transform: translateY(-30px) rotate(270deg); }
}

/* Responsive Design */
@media (max-width: 768px) {
  .home {
    padding: 8rem 1.5rem 4rem;
    min-height: 70vh;
  }
  
  .home h1 {
    font-size: clamp(2rem, 8vw, 3.5rem);
    margin-bottom: 1.5rem;
  }
  
  .home p {
    font-size: 1.1rem;
    padding: 1.5rem;
    margin: 1.5rem auto 2.5rem;
  }
  
  .home .btn {
    padding: 1rem 2.5rem;
    font-size: 1rem;
  }
  
  .home::after {
    width: 200px;
    height: 200px;
  }
  
  .home .floating-element {
    display: none;
  }
}
</style>