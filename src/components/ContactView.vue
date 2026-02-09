<script setup>
const contactCards = [
  {
    id: 'availability',
    title: 'Availability',
    content: 'Available 24/7 for inquiries and collaborations.',
    iconPath: 'M12 2C6.5 2 2 6.5 2 12s4.5 10 10 10 10-4.5 10-10S17.5 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm.5-13H11v6l5.2 3.2.8-1.3-4.5-2.7V7z',
    link: null,
    linkText: 'Contact me anytime'
  },
  {
    id: 'github',
    title: 'GitHub',
    content: 'Check out my latest projects and contributions.',
    iconPath: 'M12 2C6.477 2 2 6.477 2 12c0 4.419 2.865 8.166 6.839 9.489.5.092.682-.217.682-.482 0-.237-.008-.866-.013-1.7-2.782.603-3.369-1.34-3.369-1.34-.454-1.156-1.11-1.462-1.11-1.462-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.087 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.203 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.577.688.48C19.137 20.161 22 16.418 22 12c0-5.523-4.477-10-10-10z',
    link: 'https://github.com/mihajlo',
    linkText: 'github.com/mihajlo'
  },
  {
    id: 'email',
    title: 'Email',
    content: 'Send me an email for professional inquiries.',
    iconPath: 'M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z',
    link: 'mailto:mihajlo@example.com',
    linkText: 'mihajlo@example.com'
  },
  {
    id: 'linkedin',
    title: 'LinkedIn',
    content: 'Connect with me on LinkedIn for networking.',
    iconPath: 'M19 3a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h14m-.5 15.5v-5.3a2.7 2.7 0 0 0-2.7-2.7c-1.2 0-2 .7-2.3 1.2v-1h-3v7.8h3v-4.1c0-1 .5-1.5 1.2-1.5.7 0 1.1.5 1.1 1.4v4.2h3M7 18.5v-7.8h-3v7.8h3M6.5 6a1.5 1.5 0 1 0 0 3 1.5 1.5 0 0 0 0-3z',
    link: 'https://linkedin.com/in/mihajlo',
    linkText: 'linkedin.com/in/mihajlo'
  }
]

const openLink = (link) => {
  if (link) {
    window.open(link, '_blank');
  }
}
</script>

<template>
  <section class="contact">
    <header>
      <h2>Contact</h2>
      <p>Get in touch with me through any of these platforms.</p>
    </header>

    <div class="cards-grid">
      <div 
        v-for="card in contactCards" 
        :key="card.id" 
        class="contact-card"
        @click="openLink(card.link)"
        :class="{ 'is-link': card.link }"
      >
        <div class="card-icon-wrapper">
          <svg viewBox="0 0 24 24" width="24" height="24" class="card-icon">
            <path :d="card.iconPath" fill="currentColor" />
          </svg>
        </div>
        <h3 class="card-title">{{ card.title }}</h3>
        <p class="card-content">{{ card.content }}</p>
        
        <div class="card-action">
          <a v-if="card.link" :href="card.link" target="_blank" class="action-btn" @click.stop>
            Visit
          </a>
          <span v-else class="status-info">Online</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact {
  height: 100%;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

header h2 {
  margin: 0 0 4px;
  font-size: 1.6rem;
  color: var(--accent-soft);
}

header p {
  margin: 0;
  font-size: 0.9rem;
  color: var(--text-muted);
}

.cards-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
  flex: 1;
}

@media (max-width: 768px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr); /* 2x2 raspored */
    gap: 10px;
    padding-bottom: 80px; /* Više prostora za bottom bar */
  }
}

.contact-card {
  background: rgba(15, 23, 42, 0.6);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 20px;
  padding: 20px 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.contact-card.is-link {
  cursor: pointer;
}

.contact-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at top left, rgba(255, 140, 50, 0.1), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none; /* Sprečava blokiranje klikova */
}

.contact-card:hover {
  transform: translateY(-5px);
  border-color: var(--accent-soft);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
}

.contact-card:hover::before {
  opacity: 1;
}

.card-icon-wrapper {
  width: 44px;
  height: 44px;
  background: rgba(255, 140, 50, 0.1);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 12px;
  color: var(--accent-soft);
  transition: all 0.3s ease;
}

.contact-card:hover .card-icon-wrapper {
  background: var(--accent-soft);
  color: #0f172a;
  transform: scale(1.05) rotate(5deg);
}

.card-title {
  font-size: 1rem;
  margin: 0 0 8px;
  color: var(--text-main);
}

.card-content {
  font-size: 0.75rem;
  color: var(--text-muted);
  line-height: 1.4;
  margin: 0 0 16px;
  flex: 1;
}

.card-action {
  width: 100%;
  margin-top: auto;
}

.action-btn {
  display: block;
  width: 100%;
  padding: 8px;
  background: rgba(255, 140, 50, 0.1);
  border: 1px solid var(--accent-soft);
  color: var(--accent-soft);
  text-decoration: none;
  border-radius: 10px;
  font-size: 0.8rem;
  font-weight: 600;
  transition: all 0.2s ease;
}

.action-btn:hover {
  background: var(--accent-soft);
  color: #0f172a;
}

.status-info {
  font-size: 0.75rem;
  color: var(--text-muted);
  opacity: 0.8;
}

@media (max-width: 480px) {
  .card-title {
    font-size: 0.9rem;
  }
  .card-content {
    display: none; /* Sakrivamo opis na jako malim ekranima da bi stalo 2x2 */
  }
  .contact-card {
    padding: 12px 8px;
  }
  .card-icon-wrapper {
    width: 36px;
    height: 36px;
    margin-bottom: 8px;
  }
  .action-btn {
    padding: 6px;
    font-size: 0.7rem;
  }
}
</style>
