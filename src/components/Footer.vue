<template>
  <footer>
    <p>&copy; 2025 Nderu.ke Ent. All rights reserved.</p>
  </footer>
</template>

<style scoop>
/* Footer Section Styling */
footer {
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  color: white;
  text-align: center;
  padding: 4rem 3rem 2rem;
  margin-top: 4rem;
  position: relative;
  overflow: hidden;
}

footer::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -20%;
  width: 140%;
  height: 200%;
  background: radial-gradient(ellipse at center, rgba(0, 255, 136, 0.05) 0%, transparent 60%);
  z-index: 1;
  pointer-events: none;
}

footer::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent 0%, #00ff88 50%, transparent 100%);
  z-index: 2;
}

footer p {
  font-size: 0.95rem;
  line-height: 1.6;
  color: rgba(255, 255, 255, 0.7);
  margin: 0;
  font-weight: 300;
  position: relative;
  z-index: 3;
  transition: all 0.3s ease;
}

footer p:hover {
  color: rgba(255, 255, 255, 0.9);
  transform: translateY(-1px);
}

/* Highlight company name */
footer p::before {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 1px;
  background: #00ff88;
  transition: width 0.3s ease;
}

footer p:hover::before {
  width: 200px;
}

/* Style the company name specifically */
footer p {
  background: rgba(255, 255, 255, 0.02);
  backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 8px;
  padding: 1.5rem 2rem;
  max-width: 400px;
  margin: 0 auto;
  position: relative;
}

/* Add subtle animation to the copyright symbol */
@keyframes pulse {
  0%, 100% { opacity: 0.7; }
  50% { opacity: 1; }
}

footer p::first-letter {
  color: #00ff88;
  font-weight: 500;
  animation: pulse 3s ease-in-out infinite;
}

/* Make "Nderu.ke Ent" stand out */
footer p {
  position: relative;
}

footer p:hover {
  background: rgba(255, 255, 255, 0.03);
  border-color: rgba(0, 255, 136, 0.2);
}

/* Responsive Design */
@media (max-width: 768px) {
  footer {
    padding: 3rem 1.5rem 1.5rem;
    margin-top: 3rem;
  }
  
  footer p {
    font-size: 0.9rem;
    padding: 1rem 1.5rem;
    max-width: 300px;
  }
  
  footer::before {
    display: none;
  }
}

/* Additional enhancement: subtle floating animation */
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-3px); }
}

footer p {
  animation: float 6s ease-in-out infinite;
}

footer p:hover {
  animation-play-state: paused;
}
</style>