<template>
  <section id="services">
    <h2>Our Services</h2>
    <ul>
      <li>POS Systems (retail, wholesale)</li>
      <li>Personal Portfolios</li>
      <li>Business Portfolios</li>
      <li>E-commerce Stores</li>
      <li>Custom Software Solutions</li>
    </ul>
  </section>
</template>

<style scoop>
/* Services Section Styling */
#services {
  padding: 6rem 3rem;
  max-width: 1400px;
  margin: 0 auto;
  position: relative;
}

#services::before {
  content: '';
  position: absolute;
  top: 20%;
  right: -5%;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(0, 255, 136, 0.1) 0%, rgba(0, 255, 136, 0.05) 30%, transparent 70%);
  border-radius: 50%;
  filter: blur(1px);
  z-index: 1;
  pointer-events: none;
}

#services h2 {
  font-size: 2.5rem;
  font-weight: 300;
  line-height: 1.2;
  margin-bottom: 3rem;
  color: white;
  text-align: center;
  letter-spacing: -0.02em;
  position: relative;
  z-index: 2;
}

#services ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  max-width: 1000px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

#services li {
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 2rem;
  font-size: 1.1rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.9);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  cursor: pointer;
}

#services li::before {
  content: '→';
  position: absolute;
  right: 1.5rem;
  top: 50%;
  transform: translateY(-50%);
  color: #00ff88;
  font-size: 1.2rem;
  font-weight: bold;
  opacity: 0;
  transition: all 0.3s ease;
}

#services li::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 136, 0.1), transparent);
  transition: left 0.6s ease;
}

#services li:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-4px) scale(1.02);
  color: white;
  padding-right: 3rem;
}

#services li:hover::before {
  opacity: 1;
  transform: translateY(-50%) translateX(4px);
}

#services li:hover::after {
  left: 100%;
}

/* Add subtle icons/bullets */
#services li:nth-child(1)::before { content: '🏪'; right: auto; left: 1.5rem; opacity: 0.6; }
#services li:nth-child(2)::before { content: '👤'; right: auto; left: 1.5rem; opacity: 0.6; }
#services li:nth-child(3)::before { content: '🏢'; right: auto; left: 1.5rem; opacity: 0.6; }
#services li:nth-child(4)::before { content: '🛒'; right: auto; left: 1.5rem; opacity: 0.6; }
#services li:nth-child(5)::before { content: '⚙️'; right: auto; left: 1.5rem; opacity: 0.6; }

#services li:hover:nth-child(n)::before {
  content: '→';
  right: 1.5rem;
  left: auto;
  opacity: 1;
  color: #00ff88;
  font-size: 1.2rem;
}

/* Responsive Design */
@media (max-width: 768px) {
  #services {
    padding: 4rem 1.5rem;
  }
  
  #services h2 {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  
  #services ul {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  #services li {
    padding: 1.5rem;
    font-size: 1rem;
  }
  
  #services::before {
    display: none;
  }
}
</style>