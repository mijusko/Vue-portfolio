<template>
  <section class="home">
    <div class="intro">
      <p class="eyebrow">Welcome to my portfolio</p>
      <h2>Hi, I'm <span class="accent">Mihajlo</span></h2>
      <h3>Software Engineer</h3>
      <p class="description">
        Portfolio hook and description...
      </p>

      <div class="tags">
        <span>Vue</span>
          <span>HTML</span>
          <span>CSS</span>
          <span>Javascript</span>
          <span>Java</span>
          <span>Spring Boot</span>
          <span>SQL</span>
      </div>
    </div>

    <div class="highlight-card">
      <h4>Currently working on portfolio</h4>
      <p>In progress</p>
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

.intro {
  max-width: 520px;
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

h3 {
  font-size: 1.2rem;
  font-weight: 500;
  color: var(--text-muted);
  margin: 0 0 12px;
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