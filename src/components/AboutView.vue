<template>
  <section class="about">
    <header>
      <h2>About me</h2>
    </header>

    <div class="content">
      <p>
        My approach combines a strong foundation
         in Software Engineering with hands-on
          experience in modern frameworks. Whether it's
            architecting databases or prototyping interfaces.
      </p>
      <p>
        My approach combines a strong foundation in 
         
        <span class="accent">Software Engineering</span> 
        with hands-on experience in modern frameworks like 
        <span class="accent">Spring Boot</span>, 
        <span class="accent">Django</span> and <span class="accent">Vue.js</span>
      </p>

      <div class="info-grid">
        <div class="info-item">
          <h3>Frontend</h3>
          <ul>
            <li>Frameworks: Vue.js</li>
            <li>Core: JavaScript (ES6+), HTML5, CSS3/SCSS</li>
            <li>Design: Figma (UI/UX Design), Webflow</li>
          </ul>
        </div>
        <div class="info-item">
          <h3>Backend</h3>
          <ul>
            <li>Java: Spring Boot</li>
            <li>Python: Django, FastAPI</li>
            <li>Databases: SQL (PostgreSQL, MySQL)</li>
          </ul>
        </div>
        <div class="info-item">
          <h3>Tools & Infrastructure</h3>
          <ul>
            <li>Version Control: Git & GitHub</li>
            <li>DevOps: Docker, Linux (Server Maintenance)</li>
            <li>API: RESTful APIs, Postman</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 18px;
}

@media (max-width: 768px) {
  .about {
    height: auto;
    min-height: 100%;
    padding: 20px 10px 40px; /* Smanjen padding na dnu jer App.vue ima margin-bottom */
    justify-content: flex-start;
  }
}

header h2 {
  margin: 0px;
  font-size: 1.8rem;
  color: var(--accent-soft);
}

header p {
  margin: 0;
  font-size: 0.95rem;
  color: var(--text-muted);
}

.content {
  font-size: 0.95rem;
  color: var(--text-main);
  max-width: 800px;
  width: 100%;
}

.content p {
  margin: 0 0 12px;
  line-height: 1.6;
  color: var(--text-muted);
}

@media (max-width: 768px) {
  header h2 {
    font-size: 1.5rem;
  }
  header p {
    font-size: 0.85rem;
  }
  .content p {
    font-size: 0.85rem;
    line-height: 1.5;
  }
}

@media (max-width: 480px) {
  .content p {
    font-size: 0.8rem;
    margin-bottom: 10px;
  }
}

.accent {
  color: var(--accent-soft);
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 24px;
  width: 100%;
}

@media (max-width: 1024px) {
  .info-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .info-grid {
    grid-template-columns: 1fr;
  }
}

.info-item {
  background: rgba(15, 23, 42, 0.95);
  border-radius: 18px;
  padding: 20px;
  border: 1px solid rgba(148, 163, 184, 0.4);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.info-item h3 {
  margin: 0 0 12px;
  font-size: 1.1rem;
  color: var(--accent-soft);
}

.info-item ul {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: center;
}

.info-item li {
  font-size: 0.85rem;
  color: var(--text-muted);
  margin-bottom: 6px;
}
</style>