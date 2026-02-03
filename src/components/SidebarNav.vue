<script setup>
const props = defineProps({
  currentView: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['change-view'])

const links = [
  { id: 'home', label: 'Home' },
  { id: 'about', label: 'About me' },
  { id: 'projects', label: 'Projects' },
  { id: 'contact', label: 'Contact' }
]

const handleClick = (id) => {
  emit('change-view', id)
}
</script>

<template>
  <nav class="sidebar">
    <div class="brand">
      <div class="brand-avatar">M</div>
      <div class="brand-text">
        <h1>My Portfolio</h1>
        <p>Software Engineer</p>
      </div>
    </div>

    <ul class="nav-links">
      <li
        v-for="link in links"
        :key="link.id"
        :class="['nav-item', { active: link.id === currentView }]"
        @click="handleClick(link.id)"
      >
        <span class="nav-bullet" />
        <span class="nav-label">{{ link.label }}</span>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.sidebar {
  width: 100%;
  padding: 20px 18px;
  border-radius: 24px;
  background: linear-gradient(
      135deg,
      rgba(15, 23, 42, 0.85),
      rgba(15, 23, 42, 0.65)
    );
  border: 1px solid var(--glass-border);
  box-shadow:
    0 20px 60px rgba(15, 23, 42, 0.95),
    0 0 0 1px rgba(15, 23, 42, 0.6),
    0 0 60px rgba(56, 189, 248, 0.15);
  backdrop-filter: blur(18px);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  color: var(--text-main);
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

.brand-avatar {
  width: 42px;
  height: 42px;
  border-radius: 999px;
  background: radial-gradient(circle at 30% 0%, var(--accent-soft), var(--accent));
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 1.1rem;
  color: #0f172a;
  box-shadow: 0 0 30px rgba(255, 140, 50, 0.7);
}

.brand-text h1 {
  font-size: 1rem;
  margin: 0;
}

.brand-text p {
  font-size: 0.8rem;
  margin: 2px 0 0;
  color: var(--text-muted);
}

.nav-links {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.nav-item {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
  border-radius: 999px;
  color: var(--text-muted);
  transition:
    background 0.2s ease,
    color 0.2s ease,
    transform 0.1s ease,
    box-shadow 0.2s ease;
}

.nav-item:hover {
  background: rgba(15, 23, 42, 0.9);
  color: var(--text-main);
  transform: translateY(-1px);
  box-shadow: 0 10px 25px rgba(15, 23, 42, 0.7);
}

.nav-item.active {
  background: linear-gradient(135deg, var(--accent), var(--accent-soft));
  color: #0b1120;
  box-shadow:
    0 14px 32px rgba(255, 140, 50, 0.5),
    0 0 20px rgba(255, 140, 50, 0.8);
}

.nav-item.active .nav-bullet {
  background: #0b1120;
}

.nav-bullet {
  width: 8px;
  height: 8px;
  border-radius: 999px;
  background: rgba(148, 163, 184, 0.7);
}

.nav-label {
  font-size: 0.88rem;
  font-weight: 500;
}
</style>