<template>
  <section id="how-it-works">
    <h2>How it Works</h2>
    <ol>
      <li>Register your account</li>
      <li>Verify your email / phone</li>
      <li>Access your POS or E-commerce dashboard</li>
    </ol>
  </section>
</template>
<style scooped>
/* How It Works Section Styling */
#how-it-works {
  padding: 6rem 3rem;
  max-width: 1400px;
  margin: 0 auto;
  position: relative;
}

#how-it-works h2 {
  font-size: 2.5rem;
  font-weight: 300;
  line-height: 1.2;
  margin-bottom: 3rem;
  color: white;
  text-align: center;
  letter-spacing: -0.02em;
}

#how-it-works ol {
  list-style: none;
  counter-reset: step-counter;
  padding: 0;
  margin: 0;
  display: grid;
  gap: 2rem;
  max-width: 800px;
  margin: 0 auto;
}

#how-it-works li {
  counter-increment: step-counter;
  position: relative;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 2rem 2rem 2rem 4rem;
  font-size: 1.1rem;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.9);
  transition: all 0.3s ease;
  overflow: hidden;
}

#how-it-works li::before {
  content: counter(step-counter);
  position: absolute;
  left: 1.5rem;
  top: 50%;
  transform: translateY(-50%);
  background: #00ff88;
  color: #0a0a0a;
  width: 2rem;
  height: 2rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 0.9rem;
  z-index: 2;
}

#how-it-works li::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, #00ff88 0%, transparent 100%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

#how-it-works li:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-2px);
}

#how-it-works li:hover::after {
  opacity: 1;
}

#how-it-works li:hover::before {
  background: #00e079;
  transform: translateY(-50%) scale(1.1);
}

/* Connector lines between steps */
#how-it-works li:not(:last-child)::before {
  box-shadow: 0 2rem 0 0 rgba(0, 255, 136, 0.2);
}

/* Responsive Design */
@media (max-width: 768px) {
  #how-it-works {
    padding: 4rem 1.5rem;
  }
  
  #how-it-works h2 {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  
  #how-it-works li {
    padding: 1.5rem 1.5rem 1.5rem 3.5rem;
    font-size: 1rem;
  }
  
  #how-it-works li::before {
    left: 1rem;
    width: 1.5rem;
    height: 1.5rem;
    font-size: 0.8rem;
  }
}
</style>