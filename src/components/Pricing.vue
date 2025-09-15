<template>
  <section id="pricing">
    <h2>Pricing</h2>
    <p>Free demo available. Merchant plans start from KES 1000/month.</p>
  </section>
</template>

<style scoop>
/* Pricing Section Styling */
#pricing {
  padding: 6rem 3rem;
  max-width: 1400px;
  margin: 0 auto;
  text-align: center;
  position: relative;
}

#pricing::before {
  content: '';
  position: absolute;
  top: -10%;
  left: -10%;
  width: 40%;
  height: 120%;
  background: linear-gradient(135deg, rgba(0, 255, 136, 0.05) 0%, transparent 70%);
  transform: skewY(15deg);
  z-index: 1;
  pointer-events: none;
}

#pricing h2 {
  font-size: 2.5rem;
  font-weight: 300;
  line-height: 1.2;
  margin-bottom: 2rem;
  color: white;
  letter-spacing: -0.02em;
  position: relative;
  z-index: 2;
}

#pricing p {
  font-size: 1.25rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.8);
  max-width: 600px;
  margin: 0 auto;
  font-weight: 300;
  position: relative;
  z-index: 2;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 2rem;
  transition: all 0.3s ease;
}

#pricing p:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-2px);
}

/* Highlight the pricing amount */
#pricing p strong,
#pricing p .price {
  color: #00ff88;
  font-weight: 600;
}

/* If you want to style "KES 1000/month" specifically */
#pricing p::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 2px;
  background: #00ff88;
  transition: width 0.3s ease;
}

#pricing p:hover::after {
  width: 60%;
}

/* Responsive Design */
@media (max-width: 768px) {
  #pricing {
    padding: 4rem 1.5rem;
  }
  
  #pricing h2 {
    font-size: 2rem;
    margin-bottom: 1.5rem;
  }
  
  #pricing p {
    font-size: 1.1rem;
    padding: 1.5rem;
  }
  
  #pricing::before {
    display: none;
  }
}
</style>