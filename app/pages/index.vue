<template>
  <main>
    <section class="intro">
      <div class="container intro-inner">
        <p class="intro-label">
          Software Developer
        </p>

        <h1 class="intro-heading">
          Building software, interactive experiences,
          and occasionally strange creatures.
        </h1>

        <div class="intro-meta">
          <p>
            Developer focused on building thoughtful,
            functional digital experiences.
          </p>

          <a
            href="#work"
            class="intro-scroll"
          >
            Selected Work
            <span aria-hidden="true">↓</span>
          </a>
        </div>
      </div>
    </section>
    <section class="work" id="work">
      <div class="container">
        <div class="work-section">
          <div class="section-heading">
            <span>01</span>
            <h2>Development</h2>
          </div>

          <p class="empty-message">
            More projects coming soon.
          </p>
        </div>

        <div class="work-section">
          <div class="section-heading">
            <span>02</span>
            <h2>Creative / Experiments</h2>
          </div>

          <div class="project-list">
            <ProjectCard
              title="Time Leper"
              category="Personal Project · 3D / Real-Time"
              description="A D&D creature brought from a rough phone sketch through the complete 3D pipeline and into Unreal Engine 5."
              tools="Blender · Unreal Engine 5"
              image="/images/time-leper/cover.png"
              to="/projects/time-leper"
            />

            <ProjectCard
              title="Blender Studies"
              category="Early Work · 3D"
              description="A small archive of early renders created while learning modeling, materials, lighting, and rendering in Blender."
              tools="Blender"
              image="/images/blender-studies/donut.png"
              to="/projects/blender-studies"
            />
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.intro {
  display: flex;
  align-items: flex-end;

  min-height: 68vh;
  padding-block: 96px;
}

.intro-inner {
  width: 100%;
}

.intro-label {
  margin: 0 0 24px;

  color: var(--color-text-muted);

  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.intro-heading {
  max-width: 1050px;
  margin: 0;

  font-size: clamp(2.75rem, 6vw, 6.5rem);
  font-weight: 500;
  line-height: 0.98;
  letter-spacing: -0.045em;
}

.intro-meta {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 48px;

  margin-top: 56px;
}

.intro-meta p {
  max-width: 380px;
  margin: 0;

  color: var(--color-text-muted);

  font-size: 0.9rem;
  line-height: 1.7;
}

.intro-scroll {
  display: flex;
  align-items: center;
  gap: 12px;

  flex-shrink: 0;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;

  transition: color var(--transition-fast);
}

.intro-scroll span {
  transition: transform var(--transition-fast);
}

.intro-scroll:hover {
  color: var(--color-text);
}

.intro-scroll:hover span {
  transform: translateY(4px);
}

.intro-scroll:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

@media (max-width: 768px) {
  .intro {
    min-height: 62vh;
    padding-block: 64px;
  }

  .intro-label {
    margin-bottom: 18px;
  }

  .intro-heading {
    font-size: clamp(2.6rem, 12vw, 4.5rem);
    line-height: 1;
  }

  .intro-meta {
    align-items: flex-start;
    flex-direction: column;
    gap: 32px;

    margin-top: 40px;
  }

  .intro-meta p {
    max-width: 320px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .intro-scroll span {
    transition: none;
  }

  .intro-scroll:hover span {
    transform: none;
  }
}

.work {
  padding-block: 64px 160px;
}

.work-section + .work-section {
  margin-top: 140px;
}

.section-heading {
  display: flex;
  align-items: baseline;
  gap: 20px;

  padding-bottom: 20px;
  margin-bottom: 40px;

  border-bottom: 1px solid var(--color-border);
}

.section-heading span {
  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.1em;
}

.section-heading h2 {
  margin: 0;

  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.empty-message {
  margin: 0;
  color: var(--color-text-muted);
  font-size: 0.9rem;
}

.project-list {
  display: flex;
  flex-direction: column;
  gap: 120px;
}

@media (max-width: 768px) {
  .work {
    padding-block: 32px 96px;
  }

  .work-section + .work-section {
    margin-top: 96px;
  }

  .section-heading {
    margin-bottom: 28px;
  }

  .project-list {
    gap: 80px;
  }
}
</style>