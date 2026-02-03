<template>
  <section class="contact">
    <header>
      <h2>Contact</h2>
      <p>Contact me if you want to collaborate or have any questions.</p>
    </header>

    <div class="layout">
      <form class="form" @submit.prevent>
        <label>
          Name
          <input type="text" placeholder="Your name" />
        </label>

        <label>
          Email
          <input type="email" placeholder="you@example.com" />
        </label>

        <label>
          Message
          <textarea rows="4" placeholder="Your message" />
        </label>

        <button type="submit">Send message</button>
      </form>

      <div class="side">
        <h3>Or reach me at</h3>
        <p class="info">email@example.com</p>
        <p class="hint">
          More contact options (LinkedIn, GitHub, itd.).
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
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

.layout {
  display: grid;
  grid-template-columns: 2fr 1.2fr;
  gap: 20px;
  margin-top: 8px;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

label {
  font-size: 0.85rem;
  display: flex;
  flex-direction: column;
  gap: 4px;
  color: var(--text-main);
}

input,
textarea {
  background: rgba(15, 23, 42, 0.95);
  border-radius: 10px;
  border: 1px solid rgba(148, 163, 184, 0.5);
  padding: 8px 10px;
  color: var(--text-main);
  font-size: 0.9rem;
  outline: none;
}

input:focus,
textarea:focus {
  border-color: var(--accent-soft);
  box-shadow: 0 0 0 1px rgba(255, 140, 50, 0.7);
}

button {
  margin-top: 6px;
  align-self: flex-start;
  border: none;
  border-radius: 999px;
  padding: 8px 18px;
  font-size: 0.9rem;
  font-weight: 500;
  cursor: pointer;
  background: linear-gradient(135deg, var(--accent), var(--accent-soft));
  color: #0b1120;
  box-shadow: 0 10px 26px rgba(255, 140, 50, 0.6);
}

.side h3 {
  margin: 0 0 6px;
  font-size: 1rem;
}

.info {
  margin: 0 0 8px;
  font-size: 0.9rem;
  color: var(--accent-soft);
}

.hint {
  margin: 0;
  font-size: 0.85rem;
  color: var(--text-muted);
}
</style>