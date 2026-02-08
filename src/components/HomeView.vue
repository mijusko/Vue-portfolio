<template>
  <section class="home">
    <div class="hero-container">
      <div class="intro">
        <p class="eyebrow">Welcome to my portfolio</p>
        <h2>Hi, I'm <span class="accent">Mihajlo</span></h2>
        <h3>Software Engineer & Backend Developer</h3>
        <p class="description">
          Specijalizovan za izgradnju robusnih backend sistema i skalabilnih arhitektura. 
          Pretvaram kompleksne probleme u elegantna, visoko-performansna rešenja.
        </p>


      </div>

      <div class="hero-image">
        <div class="image-glow-container">
          <div class="image-wrapper">
            <img src="../assets/NoBackground.png" alt="Mihajlo" />
          </div>
        </div>
      </div>
    </div>


  </section>
</template>

<style scoped>
.home {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.hero-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 40px;
  flex: 1;
}

@media (max-width: 768px) {
  .hero-container {
    flex-direction: column-reverse;
    justify-content: center;
    text-align: center;
    gap: 20px;
  }
}

.intro {
  max-width: 520px;
}

@media (max-width: 768px) {
  .intro {
    max-width: 100%;
  }
}

img {
  border-radius: 10%;
}

.hero-image {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-wrapper{
  max-width: 250px;
  max-height: 250px;
  border-radius: 30%;
}

.image-glow-container {
  position: relative;
  width: 450px;
  height: 450px;
  display: flex;
  justify-content: center;
  align-items: center;
}

@media (max-width: 768px) {
  .image-glow-container {
    width: 280px;
    height: 280px;
  }
}

/* Ovde kačimo after i before efekte */
.image-glow-container::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, var(--accent-soft), transparent);
  box-shadow: 0 0 60px rgba(255, 140, 50, 0.9);
  opacity: 0.8;
}

.image-glow-container::after {
  content: '';
  position: absolute;
  inset: -30px;
  border-radius: 50%;
  border: 10px dashed var(--accent-soft);
  opacity: 0.4;
  animation: rotate 20s linear infinite;
}

@media (max-width: 768px) {
  .image-glow-container::after {
    inset: -15px;
    border-width: 6px;
  }
}

.image-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.image-wrapper img {
  width: 100%;
  height: auto;
  object-fit: contain;
  /* Višeslojna senka za bolji dubinski efekat */
  filter: drop-shadow(0 20px 30px rgba(0,0,0,0.7)) 
          drop-shadow(0 10px 10px rgba(0,0,0,0.4));
  z-index: 1;
}

.eyebrow {
  text-transform: uppercase;
  letter-spacing: 0.18em;
  font-size: 0.7rem;
  color: var(--accent-soft);
  margin-bottom: 8px;
}

h2 {
  font-size: 2rem;
  margin: 0 0 4px;
}

@media (max-width: 768px) {
  h2 {
    font-size: 1.6rem;
  }
}

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-muted);
  margin: 0 0 12px;
}

@media (max-width: 768px) {
  h3 {
    font-size: 1rem;
  }
}

.accent {
  color: var(--accent-soft);
}

.description {
  color: var(--text-muted);
  font-size: 0.95rem;
  line-height: 1.6;
  max-width: 480px;
}

@media (max-width: 768px) {
  .description {
    font-size: 0.85rem;
    margin: 0 auto;
  }
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-top: 18px;
}

.tags span {
  font-size: 0.78rem;
  padding: 6px 10px;
  border-radius: 999px;
  border: 1px solid rgba(148, 163, 184, 0.5);
  background: radial-gradient(circle at top left, rgba(148, 163, 184, 0.4), transparent);
}

.highlight-card {
  align-self: flex-end;
  max-width: 320px;
  padding: 16px 18px;
  border-radius: 18px;
  background: radial-gradient(circle at top left, rgba(56, 189, 248, 0.2), transparent),
    rgba(15, 23, 42, 0.95);
  border: 1px solid rgba(148, 163, 184, 0.4);
  box-shadow: 0 18px 40px rgba(15, 23, 42, 0.8);
  font-size: 0.9rem;
}

.highlight-card h4 {
  margin: 0 0 8px;
  font-size: 0.9rem;
}
</style>