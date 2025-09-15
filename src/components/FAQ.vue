<template>
  <section id="faq">
    <h2>FAQ</h2>
    <p><strong>Q: Can I try before paying?</strong> Yes, we offer a demo account.</p>
    <p><strong>Q: Do I need approval for ePOS/eCommerce?</strong> Yes, merchants are verified.</p>
  </section>
</template>

<style scoop>
/* FAQ Section Styling */
#faq {
  padding: 6rem 3rem;
  max-width: 1400px;
  margin: 0 auto;
  position: relative;
}

#faq::before {
  content: '';
  position: absolute;
  top: -10%;
  right: -5%;
  width: 40%;
  height: 120%;
  background: linear-gradient(135deg, rgba(0, 255, 136, 0.05) 0%, transparent 70%);
  transform: skewY(-10deg);
  z-index: 1;
  pointer-events: none;
}

#faq h2 {
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

#faq p {
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  padding: 2rem;
  margin: 1.5rem auto;
  font-size: 1.1rem;
  line-height: 1.7;
  color: rgba(255, 255, 255, 0.8);
  max-width: 800px;
  position: relative;
  z-index: 2;
  transition: all 0.3s ease;
  cursor: pointer;
  overflow: hidden;
}

#faq p::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, #00ff88, transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
}

#faq p::after {
  content: '';
  position: absolute;
  top: 0;
  right: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 255, 136, 0.05), transparent);
  transition: right 0.6s ease;
}

#faq p:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(0, 255, 136, 0.3);
  transform: translateY(-2px);
  color: rgba(255, 255, 255, 0.95);
}

#faq p:hover::before {
  opacity: 1;
}

#faq p:hover::after {
  right: 100%;
}

/* Style the questions */
#faq p strong {
  color: #00ff88;
  font-weight: 600;
  display: block;
  margin-bottom: 0.5rem;
  font-size: 1.15rem;
  position: relative;
}

#faq p strong::before {
  content: 'Q';
  position: absolute;
  left: -2rem;
  top: 0;
  background: #00ff88;
  color: #0a0a0a;
  width: 1.5rem;
  height: 1.5rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: 700;
}

/* Style the answers */
#faq p {
  padding-left: 3rem;
}

/* Add answer indicator */
#faq p:not(:has(strong))::before {
  content: 'A';
  position: absolute;
  left: 1rem;
  top: 2rem;
  background: rgba(255, 255, 255, 0.1);
  color: #00ff88;
  width: 1.5rem;
  height: 1.5rem;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: 700;
  border: 1px solid rgba(0, 255, 136, 0.3);
}

/* Alternative styling for inline Q&A format */
#faq p:has(strong) {
  position: relative;
}

#faq p:has(strong) strong::after {
  content: '';
  display: block;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, rgba(0, 255, 136, 0.3), transparent);
  margin: 0.5rem 0;
}

/* Responsive Design */
@media (max-width: 768px) {
  #faq {
    padding: 4rem 1.5rem;
  }
  
  #faq h2 {
    font-size: 2rem;
    margin-bottom: 2rem;
  }
  
  #faq p {
    padding: 1.5rem 1.5rem 1.5rem 2.5rem;
    font-size: 1rem;
    margin: 1rem auto;
  }
  
  #faq p strong {
    font-size: 1.1rem;
  }
  
  #faq p strong::before {
    left: -1.5rem;
    width: 1.2rem;
    height: 1.2rem;
  }
  
  #faq::before {
    display: none;
  }
}
</style>