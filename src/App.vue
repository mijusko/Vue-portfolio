<script setup>
import { ref } from 'vue'
import SidebarNav from './components/SidebarNav.vue'
import HomeView from './components/HomeView.vue'
import AboutView from './components/AboutView.vue'
import ProjectsView from './components/ProjectsView.vue'
import ContactView from './components/ContactView.vue'

const currentView = ref('home')

const viewsMap = {
  home: HomeView,
  about: AboutView,
  projects: ProjectsView,
  contact: ContactView
}
</script>

<template>
  <div class="app-shell">
    <aside class="sidebar-wrapper">
      <SidebarNav :current-view="currentView" @change-view="currentView = $event" />
    </aside>

    <main class="content-wrapper">
      <component :is="viewsMap[currentView]" class="view" />
    </main>
  </div>
</template>

<style>
.app-shell {
  display: flex;
  height: 100%;
  width: 100%;
  gap: 16px; /* Smanjeno sa 24px */
}

@media (max-width: 768px) {
  .app-shell {
    flex-direction: column;
    padding: 12px;
    gap: 12px;
  }
}

.sidebar-wrapper {
  width: 220px; /* Smanjeno sa 250px */
  height: 100%;
  display: flex;
  align-items: center;
}

@media (max-width: 768px) {
  .sidebar-wrapper {
    width: 100%;
    height: auto;
    order: 2;
    position: fixed;
    bottom: 12px;
    left: 0;
    padding: 0 12px;
    z-index: 100;
  }
}

.content-wrapper {
  flex: 1;
  height: 100%;
  background: linear-gradient(135deg, rgba(15, 23, 42, 0.9), rgba(15, 23, 42, 0.98));
  border-radius: 24px;
  padding: 24px 28px;
  overflow: hidden;
  box-shadow:
    0 24px 60px rgba(15, 23, 42, 0.9),
    0 0 0 1px rgba(15, 23, 42, 0.7);
}

@media (max-width: 768px) {
  .content-wrapper {
    padding: 20px;
    margin-bottom: 80px; /* Prostor za bottom bar */
  }
}

.view {
  height: 100%;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}
</style>