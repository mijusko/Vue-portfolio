<script setup>
import { ref, computed } from 'vue';

const activeIndex = ref(0);

const projects = ref([
  {
    id: 1,
    title: "E-commerce Platform",
    description: "Kompletno rešenje za online prodaju sa integrisanim sistemom plaćanja i upravljanjem zalihama. Fokus na brzini i sigurnosti.",
    video: "https://www.w3schools.com/html/mov_bbb.mp4", // Placeholder video
    technologies: ["Spring Boot", "Vue.js", "PostgreSQL", "Docker"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    id: 2,
    title: "Real-time Chat App",
    description: "Aplikacija za razmenu poruka u realnom vremenu koristeći WebSocket tehnologiju. Podržava grupne razgovore i deljenje fajlova.",
    video: "https://www.w3schools.com/html/movie.mp4", // Placeholder video
    technologies: ["Node.js", "Socket.io", "Redis", "React"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    id: 3,
    title: "AI Image Generator",
    description: "Interfejs za generisanje slika pomoću veštačke inteligencije. Koristi napredne modele za transformaciju teksta u vizuelni sadržaj.",
    video: "https://www.w3schools.com/html/mov_bbb.mp4",
    technologies: ["Python", "PyTorch", "FastAPI", "Next.js"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    id: 4,
    title: "Crypto Tracker",
    description: "Aplikacija za praćenje cena kriptovaluta u realnom vremenu sa detaljnim grafikonima i analizom portfolia.",
    video: "https://www.w3schools.com/html/movie.mp4",
    technologies: ["Vue 3", "Chart.js", "CoinGecko API", "Tailwind"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    id: 5,
    title: "Task Management Tool",
    description: "Alat za organizaciju timskog rada, sličan Trello platformi. Omogućava drag-and-drop upravljanje zadacima i rokovima.",
    video: "https://www.w3schools.com/html/mov_bbb.mp4",
    technologies: ["Java", "Hibernate", "Angular", "MySQL"],
    github: "https://github.com",
    live: "https://example.com"
  },
  {
    id: 6,
    title: "Fitness Tracker API",
    description: "REST API za praćenje fitnes aktivnosti, ishrane i napretka korisnika. Dokumentovan pomoću Swagger-a.",
    video: "https://www.w3schools.com/html/movie.mp4",
    technologies: ["Go", "Gin", "MongoDB", "JWT"],
    github: "https://github.com",
    live: "https://example.com"
  }
]);

const activeProject = computed(() => projects.value[activeIndex.value]);

const nextProject = () => {
  activeIndex.value = (activeIndex.value + 1) % projects.value.length;
};

const prevProject = () => {
  activeIndex.value = (activeIndex.value - 1 + projects.value.length) % projects.value.length;
};

const setProject = (index) => {
  activeIndex.value = index;
};
</script>

<template>
  <section class="projects">
    <header>
      <h2>My Projects</h2>
      <p>Istražite moje najnovije radove kroz ovaj interaktivni karusel.</p>
    </header>

    <div class="carousel-container">
      <button class="nav-btn prev" @click="prevProject">
        <span class="arrow">‹</span>
      </button>

      <div class="project-display">
        <div class="project-content">
          <div class="project-info">
            <h3 class="project-title">{{ activeProject.title }}</h3>
            <p class="project-description">{{ activeProject.description }}</p>
            
            <div class="tech-stack">
              <span v-for="tech in activeProject.technologies" :key="tech" class="tech-tag">
                {{ tech }}
              </span>
            </div>

            <div class="project-links">
              <a :href="activeProject.live" target="_blank" class="link-btn primary">
                <i class="icon">🌐</i> Live Demo
              </a>
              <a :href="activeProject.github" target="_blank" class="link-btn secondary">
                <i class="icon">📁</i> GitHub
              </a>
            </div>
          </div>

          <div class="project-visual">
            <div class="video-wrapper">
              <video :key="activeProject.video" controls class="project-video">
                <source :src="activeProject.video" type="video/mp4">
                Vaš pretraživač ne podržava video tag.
              </video>
            </div>
          </div>
        </div>
      </div>

      <button class="nav-btn next" @click="nextProject">
        <span class="arrow">›</span>
      </button>
    </div>

    <div class="carousel-indicators">
      <button 
        v-for="(project, index) in projects" 
        :key="project.id"
        class="indicator"
        :class="{ active: activeIndex === index }"
        @click="setProject(index)"
      ></button>
    </div>
  </section>
</template>

<style scoped>
.projects {
  height: 100%;
  display: flex;
  flex-direction: column;
  gap: 24px;
  color: white;
}

header h2 {
  margin: 0 0 4px;
  font-size: 1.8rem;
  color: var(--accent-soft);
}

header p {
  margin: 0;
  font-size: 0.95rem;
  color: var(--text-muted);
}

.carousel-container {
  flex: 1;
  display: flex;
  align-items: center;
  gap: 20px;
  position: relative;
  min-height: 0; /* Važno za flexbox decu */
}

.project-display {
  flex: 1;
  height: 100%;
  background: rgba(15, 23, 42, 0.6);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 24px;
  padding: 32px;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}

.project-content {
  display: flex;
  height: 100%;
  gap: 40px;
}

.project-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.project-title {
  font-size: 2.2rem;
  margin: 0 0 16px;
  background: linear-gradient(to right, #fff, var(--accent-soft));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.project-description {
  font-size: 1.1rem;
  line-height: 1.6;
  color: var(--text-muted);
  margin-bottom: 24px;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 32px;
}

.tech-tag {
  padding: 6px 14px;
  background: rgba(255, 140, 50, 0.1);
  border: 1px solid rgba(255, 140, 50, 0.3);
  color: var(--accent-soft);
  border-radius: 99px;
  font-size: 0.85rem;
  font-weight: 500;
}

.project-links {
  display: flex;
  gap: 16px;
}

.link-btn {
  padding: 12px 24px;
  border-radius: 12px;
  text-decoration: none;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.link-btn.primary {
  background: var(--accent-soft);
  color: #0f172a;
}

.link-btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(255, 140, 50, 0.4);
}

.link-btn.secondary {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: white;
}

.link-btn.secondary:hover {
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-2px);
}

.project-visual {
  flex: 1.2;
  display: flex;
  align-items: center;
  justify-content: center;
}

.video-wrapper {
  width: 100%;
  aspect-ratio: 16/9;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.project-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.nav-btn {
  margin:5px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: white;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  z-index: 10;
}

.nav-btn:hover {
  background: var(--accent-soft);
  color: #0f172a;
  transform: scale(1);
}

.arrow {
  font-size: 3rem;
  line-height: 3;
  margin-bottom: 15%;
}

.carousel-indicators {
  display: flex;
  justify-content: center;
  gap: 12px;
  padding-bottom: 10px;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.2);
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.indicator.active {
  background: var(--accent-soft);
  width: 30px;
  border-radius: 6px;
}

/* Responzivnost */
@media (max-width: 1024px) {
  .project-content {
    flex-direction: column;
    overflow-y: auto;
    gap: 24px;
  }
  
  .project-visual {
    order: -1;
  }
}

@media (max-width: 768px) {
  .projects-container {
    padding: 10px;
  }

  .carousel-container {
    gap: 10px;
  }

  .project-display {
    padding: 20px;
  }

  .project-title {
    font-size: 1.5rem;
  }

  .nav-btn {
    width: 40px;
    height: 40px;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }

  .nav-btn.prev {
    left: -10px;
  }

  .nav-btn.next {
    right: -10px;
  }

  .arrow {
    font-size: 2rem;
  }

  .tech-tag {
    font-size: 0.7rem;
    padding: 4px 8px;
  }

  .link-btn {
    padding: 8px 16px;
    font-size: 0.8rem;
    flex: 1;
    text-align: center;
  }
}
</style>