<template>
  <section class="about">
    <header>
      <h2>About me</h2>
      <p>More about me.</p>
    </header>

    <div class="content">
      <p>
        "I am a Fullstack developer focused on creating clean and intuitive user interfaces.
         I'm learning Vue.js and Spring boot.."
      </p>
      <p>
        I am really interested in
        <span class="accent">single-page apps</span> and modern web apps.
      </p>

      <div class="info-grid">
        <div class="info-item">
          <h3>Tech stack</h3>
          <ul>
            <li>Vue.js</li>
            <li>JavaScript (ES6+)</li>
            <li>HTML &amp; CSS</li>
          </ul>
        </div>
        <div class="info-item">
          <h3>Backend</h3>
          <ul>
            <li>Java</li>
            <li>Spring boot</li>
            <li>SQL</li>
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
  gap: 18px;
}

header h2 {
  margin: 0 0 4px;
  font-size: 1.4rem;
}

header p {
  margin: 0;
  font-size: 0.9rem;
  color: var(--text-muted);
}

.content {
  font-size: 0.95rem;
  color: var(--text-main);
  max-width: 650px;
}

.content p {
  margin: 0 0 12px;
  line-height: 1.6;
  color: var(--text-muted);
}

.accent {
  color: var(--accent-soft);
}

.info-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 16px;
  margin-top: 12px;
}

@media (max-width: 640px) {
  .info-grid {
    grid-template-columns: 1fr;
  }
}

.info-item {
  background: rgba(15, 23, 42, 0.95);
  border-radius: 18px;
  padding: 14px 16px;
  border: 1px solid rgba(148, 163, 184, 0.4);
}

.info-item h3 {
  margin: 0 0 8px;
  font-size: 0.95rem;
}

.info-item ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.info-item li {
  font-size: 0.85rem;
  color: var(--text-muted);
}
</style>