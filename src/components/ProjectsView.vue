<template>
  <section class="projects">
    <header>
      <h2>Projects</h2>
      <p>projects description and others...</p>
    </header>

    <div class="grid">
      <article class="card">
        <h3>Portfolio Website</h3>
        <p class="type">Personal project</p>
        <p class="description">
          First project...
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
      </article>

      <article class="card">
        <h3>Example Project</h3>
        <p class="type">Concept</p>
        <p class="description">
          Placeholders for projects...
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
      </article>
    </div>
  </section>
</template>

<style scoped>
.projects {
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

.grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 18px;
  margin-top: 8px;
}

.card {
  background: radial-gradient(circle at top left, rgba(59, 130, 246, 0.2), transparent),
    rgba(15, 23, 42, 0.96);
  border-radius: 18px;
  padding: 16px 18px;
  border: 1px solid rgba(148, 163, 184, 0.4);
  box-shadow: 0 16px 38px rgba(15, 23, 42, 0.85);
}

.card h3 {
  margin: 0 0 4px;
  font-size: 1rem;
}

.type {
  margin: 0 0 10px;
  font-size: 0.8rem;
  color: var(--accent-soft);
}

.description {
  margin: 0 0 12px;
  font-size: 0.9rem;
  color: var(--text-muted);
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.tags span {
  font-size: 0.75rem;
  padding: 4px 8px;
  border-radius: 999px;
  border: 1px solid rgba(148, 163, 184, 0.5);
}
</style>