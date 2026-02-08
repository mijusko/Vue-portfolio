<script setup>
const props = defineProps({
  currentView: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['change-view'])

const links = [
  { 
    id: 'home', 
    label: 'Home', 
    iconPath: 'M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z' 
  },
  { 
    id: 'about', 
    label: 'About me', 
    iconPath: 'M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z' 
  },
  { 
    id: 'projects', 
    label: 'Projects', 
    iconPath: 'M20 18c1.1 0 1.99-.9 1.99-2L22 6c0-1.1-.9-2-2-2H4c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2H0v2h24v-2h-4zM4 6h16v10H4V6z' 
  },
  { 
    id: 'contact', 
    label: 'Contact', 
    iconPath: 'M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z' 
  }
]

const handleClick = (id) => {
  emit('change-view', id)
}
</script>

<template>
  <nav class="sidebar">

    <ul class="nav-links">
      <li
        v-for="link in links"
        :key="link.id"
        :class="['nav-item', { active: link.id === currentView }]"
        @click="handleClick(link.id)"
      >
        <svg class="nav-icon" viewBox="0 0 24 24" width="24" height="24">
          <path :d="link.iconPath" fill="currentColor" />
        </svg>
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

@media (max-width: 768px) {
  .sidebar {
    padding: 10px;
    flex-direction: row;
    border-radius: 20px;
  }
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 24px;
}

@media (max-width: 768px) {
  .brand {
    display: none; /* Sakrivamo logo na mobilnom bottom baru radi uštede prostora */
  }
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

@media (max-width: 768px) {
  .nav-links {
    flex-direction: row;
    width: 100%;
    justify-content: space-around;
    gap: 0;
  }
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

@media (max-width: 768px) {
  .nav-item {
    flex-direction: column;
    gap: 4px;
    padding: 8px 12px;
    flex: 1;
    justify-content: center;
  }
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

.nav-item.active .nav-icon {
  color: #0b1120;
}

.nav-item:hover .nav-icon {
  transform: scale(1.1);
}

.nav-icon {
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
  color: inherit;
}

@media (max-width: 768px) {
  .nav-icon {
    width: 24px;
    height: 24px;
  }
}

.nav-label {
  font-size: 0.88rem;
  font-weight: 500;
}

@media (max-width: 768px) {
  .nav-label {
    font-size: 0.7rem;
  }
}
</style>