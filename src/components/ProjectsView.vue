<script setup>
import { ref, computed } from 'vue';

const activeIndex = ref(0);

const projects = ref([
  {
    id: 1,
    title: "JobCollector WebScrapper",
    description: "An automation tool designed to streamline the job search process by aggregating and centralizing job listings from multiple online platforms. This project addresses the challenge of fragmented job markets by scraping, parsing, and storing relevant vacancies.",
    video: "/videos/JobCollector.mp4",
    technologies: ["Python", "FastAPI", "Selenium", "Vue.js"],
    github: "https://github.com/mijusko/Job-Collector",
    live: "https://job-collector.netlify.app/"
  },
  {
    id: 2,
    title: "Find-Warranty app for receipts",
    description: "A streamlined web application designed to simplify the management of product warranties and digital receipts. Implement AI chat as financial assistant and for data recognition from recipts",
    video: "/videos/FindWarranty.mp4",
    technologies: ["Vue.js", "Spring boot", "PostgreSQL", "AI integration", "Docker"],
    github: "https://github.com/mijusko/FindWarranty",
    live: "https://findwarranty.netlify.app/"
  },
  {
    id: 3,
    title: "VideoCall WebApp",
    description: "A real-time video conferencing platform built to facilitate seamless peer-to-peer communication. This project focuses on the complexities of live data streaming, utilizing WebSockets for signaling and connection management.",
    video: "/videos/VideoCall.mp4",
    technologies: ["Java", "Spring boot", "WebSocket", "STUN/TURN Servers"],
    github: "https://github.com/mijusko/spring-boot-videocall",
    live: "https://spring-boot-videocall.onrender.com/"
  },
  {
    id: 4,
    title: "Youtube Converter in Java",
    description: "A desktop utility tool developed in Java that allows users to download and convert YouTube content into various media formats.",
    video: "/videos/YTconverter.mp4",
    technologies: ["Java", "Java Swing", "AWT"],
    github: "https://github.com/mijusko/Youtube-Converter-Java",
  },
  {
    id: 5,
    title: "Figma Design",
    description: "Spearheaded the UI/UX design phase using Figma, creating high-fidelity wireframes and prototypes that were fully adopted for the final production site.",
    video: "/videos/TPfigma.mp4",
    technologies: ["Figma", "UI/UX Design"],
    live: "https://www.figma.com/design/GHJKKqVx8Bud2TJrA3zy7H/TeretanaPark?t=8AcCT9hdVSE1OxNc-1"
  },
  {
    id: 6,
    title: "BobbleBobble game in Java",
    description: "A custom-built 2D adventure game developed from scratch using Java. This project focuses on the core principles of game development, including a synchronized game loop, entity management, and real-time rendering.",
    video: "/videos/BobbleBobble.mp4",
    technologies: ["Java", "Java Swing", "AWT"],
    github: "https://github.com/mijusko/Java-Game",
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
  gap: 14px;
  color: white;
}

header h2 {
  margin: 0px;
  font-size: 1.8rem;
  color: var(--accent-soft);
}
h3.project-title{
margin:0;
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
  margin: 0 35px;
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
  margin: 0px;
  background: linear-gradient(to right, #fff, var(--accent-soft));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.project-description {
  font-size: 1.1rem;
  line-height: 1.6;
  color: var(--text-muted);
  margin-bottom: 14px;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 22px;
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
    gap: 8px; /* Smanjeno sa 24px (bilo je 4px u prethodnom čitanju, ali popravljam na optimalnih 8px) */
  }
  
  .project-visual {
    order: -1;
  }
}

@media (max-width: 768px) {
  .project-content {
    gap: 4px; /* Još manji razmak za mobilne telefone */
  }
  .projects-container {
    padding: 10px;
    height: 100%;
    overflow-y: auto; /* Omogućavamo skrolovanje cele sekcije ako zatreba */
  }

  .carousel-container {
    gap: 5px;
  }

  .project-display {
    padding: 16px;
  }

  .project-title {
    font-size: 1.2rem; /* Smanjeno sa 1.5rem */
    margin-bottom: 8px;
  }

  .project-description {
    font-size: 0.8rem; /* Smanjeno */
    line-height: 1.4;
    margin-bottom: 12px;
  }

  .tech-stack {
    gap: 4px;
    margin-bottom: 12px;
  }

  .tech-tag {
    font-size: 0.65rem; /* Smanjeno */
    padding: 3px 6px;
  }

  .project-links {
    gap: 8px;
  }

  .link-btn {
    padding: 6px 12px;
    font-size: 0.75rem; /* Smanjeno */
    flex: 1;
    text-align: center;
  }

  .nav-btn {
    width: 32px; /* Smanjeno sa 40px */
    height: 32px;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }

  .nav-btn.prev {
    left: -5px;
  }

  .nav-btn.next {
    right: -5px;
  }

  .arrow {
    font-size: 1.5rem; /* Smanjeno */
  }

  .video-wrapper {
    margin-top: 10px;
  }
}
</style>