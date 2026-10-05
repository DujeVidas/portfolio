<script setup lang="ts">
const lightbox = reactive({
  open: false,
  src: '',
  alt: '',
  caption: '',
  trigger: null as HTMLButtonElement | null
})

function openLightbox(
  src: string,
  alt: string,
  caption = '',
  trigger: HTMLButtonElement | null = null
) {
  lightbox.src = src
  lightbox.alt = alt
  lightbox.caption = caption
  lightbox.trigger = trigger
  lightbox.open = true
}

function closeLightbox() {
  lightbox.open = false

  nextTick(() => {
    lightbox.trigger?.focus()
    lightbox.trigger = null
  })
}

const renders = [
  {
    src: '/images/blender-studies/donut.png',
    alt: 'Blender render of a donut and coffee mug',
    title: 'Donut & Coffee Mug'
  },
  {
    src: '/images/blender-studies/modern-street-light.png',
    alt: 'Blender render of a modern street light',
    title: 'Modern Street Light'
  },
  {
    src: '/images/blender-studies/old-street-light.png',
    alt: 'Blender render of an old street light',
    title: 'Old Street Light'
  },
  {
    src: '/images/blender-studies/chair-table.png',
    alt: 'Blender render of a wooden chair and table',
    title: 'Wooden Chair & Table'
  },
  {
    src: '/images/blender-studies/glass-water.png',
    alt: 'Blender render of a glass of water',
    title: 'Glass of Water'
  }
]
</script>

<template>
  <main>
    <section class="project-hero">
      <div class="container">
        <p class="project-label">
          Personal Work · 3D
        </p>

        <h1>
          Blender Studies
        </h1>

        <div class="hero-info">
          <p class="hero-description">
            A small archive of early renders created while I was learning
            Blender, exploring modeling, materials, lighting, and rendering.
          </p>

          <p class="hero-note">
            The original project files have since been lost, but I was able
            to recover these final renders.
          </p>
        </div>
      </div>
    </section>

    <section class="gallery-section">
      <div class="container">
        <div class="gallery-heading">
          <span>01</span>
          <p>Selected Renders</p>
        </div>

        <div class="render-gallery">
          <figure
            v-for="(render, index) in renders"
            :key="render.src"
            class="render-item"
          >
            <EnlargeableImage
              :src="render.src"
              :alt="render.alt"
              :caption="render.title"
              image-class="render-image"
              object-fit="contain"
              @enlarge="openLightbox"
            />

            <figcaption>
              <span>
                {{ String(index + 1).padStart(2, '0') }}
              </span>

              {{ render.title }}
            </figcaption>
          </figure>
        </div>
      </div>
    </section>

    <section class="project-end">
      <div class="container">
        <NuxtLink
          to="/"
          class="back-to-work"
        >
          <span class="back-label">
            End of project
          </span>

          <span class="back-title">
            Back to all work
            <span aria-hidden="true">↗</span>
          </span>
        </NuxtLink>
      </div>
    </section>

    <ImageLightbox
      :open="lightbox.open"
      :src="lightbox.src"
      :alt="lightbox.alt"
      :caption="lightbox.caption"
      @close="closeLightbox"
    />
  </main>
</template>
<style scoped>
.project-hero {
  display: flex;
  align-items: flex-end;

  min-height: 72vh;
  padding-block: 96px 120px;
}

.project-label {
  margin: 0 0 28px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.project-hero h1 {
  max-width: 1100px;
  margin: 0;

  font-size: clamp(4rem, 9vw, 9rem);
  font-weight: 500;
  line-height: 0.9;
  letter-spacing: -0.055em;
  text-transform: uppercase;
}

.hero-info {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(240px, 0.45fr);
  gap: clamp(48px, 8vw, 140px);

  max-width: 900px;
  margin-top: 64px;
}

.hero-description,
.hero-note {
  margin: 0;

  color: var(--color-text-muted);

  font-size: 0.95rem;
  line-height: 1.7;
}

.hero-description {
  color: var(--color-text);
}


/* ========================================
   GALLERY
   ======================================== */

.gallery-section {
  padding-block: 160px;

  border-top: 1px solid var(--color-border);
}

.gallery-heading {
  display: flex;
  align-items: baseline;
  gap: 20px;

  padding-bottom: 20px;
  margin-bottom: 72px;

  border-bottom: 1px solid var(--color-border);
}

.gallery-heading span {
  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.1em;
}

.gallery-heading p {
  margin: 0;

  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.render-gallery {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 96px 24px;
}

.render-item {
  min-width: 0;
  margin: 0;
}

/*
  Make the first render the introduction to the gallery
  by allowing it to occupy the full width.
*/
.render-item:first-child {
  grid-column: 1 / -1;
}

.render-image {
  width: 100%;
  min-height: 0;

  background: var(--color-surface);
}

.render-item figcaption {
  display: flex;
  gap: 12px;

  margin-top: 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.render-item figcaption span {
  color: var(--color-text);
}


/* ========================================
   PROJECT END
   ======================================== */

.project-end {
  padding-block: 120px;

  border-top: 1px solid var(--color-border);
}

.back-to-work {
  display: flex;
  flex-direction: column;
  gap: 24px;

  width: 100%;
}

.back-label {
  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.back-title {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 32px;

  font-size: clamp(3rem, 7vw, 7.5rem);
  font-weight: 500;
  line-height: 0.95;
  letter-spacing: -0.05em;
}

.back-title > span {
  flex-shrink: 0;

  color: var(--color-text-muted);

  font-size: 0.45em;

  transition:
    color var(--transition-fast),
    transform var(--transition-fast);
}

.back-to-work:hover .back-title > span {
  color: var(--color-text);
  transform: translate(6px, -6px);
}

.back-to-work:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 8px;
}


/* ========================================
   RESPONSIVE
   ======================================== */

@media (max-width: 768px) {
  .project-hero {
    min-height: 65vh;
    padding-block: 64px 80px;
  }

  .project-hero h1 {
    font-size: clamp(3.5rem, 17vw, 6rem);
  }

  .hero-info {
    grid-template-columns: 1fr;
    gap: 24px;

    margin-top: 48px;
  }

  .gallery-section {
    padding-block: 96px;
  }

  .gallery-heading {
    margin-bottom: 48px;
  }

  .render-gallery {
    grid-template-columns: 1fr;
    gap: 64px;
  }

  .render-item:first-child {
    grid-column: auto;
  }

  .project-end {
    padding-block: 80px;
  }

  .back-title {
    font-size: clamp(2.7rem, 13vw, 5rem);
  }
}

@media (prefers-reduced-motion: reduce) {
  .back-title > span {
    transition: none;
  }

  .back-to-work:hover .back-title > span {
    transform: none;
  }
}
</style>