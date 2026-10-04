<script setup lang="ts">
defineProps<{
  title: string
  category: string
  description: string
  tools: string
  image: string
  to: string
}>()

const isHovering = ref(false)

const cursorX = ref(0)
const cursorY = ref(0)

function handleMouseMove(event: MouseEvent) {
  cursorX.value = event.clientX
  cursorY.value = event.clientY
}
</script>

<template>
  <NuxtLink
    :to="to"
    class="project-card"
    @mouseenter="isHovering = true"
    @mouseleave="isHovering = false"
    @mousemove="handleMouseMove"
  >
    <div class="project-image-wrapper">
      <img
        :src="image"
        :alt="title"
        class="project-image"
      >

      <div class="project-overlay">
        <div class="project-info">
          <p class="project-category">
            {{ category }}
          </p>

          <h3>{{ title }}</h3>

          <p class="project-description">
            {{ description }}
          </p>

          <div class="project-bottom">
            <span>{{ tools }}</span>
            <span>View Project →</span>
          </div>
        </div>
      </div>
    </div>
    <Teleport to="body">
        <div
            v-if="isHovering"
            class="cursor-label"
            :style="{
            left: `${cursorX}px`,
            top: `${cursorY}px`
            }"
        >
            View Project ↗
        </div>
    </Teleport>
  </NuxtLink>
</template>

<style scoped>
.project-card {
  display: block;
}

.project-image-wrapper {
  position: relative;
  overflow: hidden;
  aspect-ratio: 16 / 9;
  background: var(--color-surface);
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;

  transition:
    transform var(--transition-normal),
    opacity var(--transition-normal);
}

.project-overlay {
  position: absolute;
  inset: 0;

  display: flex;
  align-items: flex-end;

  padding: clamp(24px, 4vw, 56px);

  background: rgba(0, 0, 0, 0.68);
  opacity: 0;

  transition: opacity var(--transition-normal);
}

.project-info {
  width: 100%;
  max-width: 700px;

  transform: translateY(12px);
  transition: transform var(--transition-normal);
}

.project-category {
  margin: 0 0 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.project-info h3 {
  margin: 0;

  font-size: clamp(2rem, 4vw, 4.5rem);
  font-weight: 500;
  letter-spacing: -0.04em;
}

.project-description {
  max-width: 520px;
  margin: 16px 0 32px;

  color: #c8c8c8;

  font-size: 1rem;
  line-height: 1.6;
}

.project-bottom {
  display: flex;
  justify-content: space-between;
  gap: 24px;

  color: var(--color-text-muted);

  font-size: 0.75rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.project-card:hover .project-overlay,
.project-card:focus-visible .project-overlay {
  opacity: 1;
}

.project-card:hover .project-info,
.project-card:focus-visible .project-info {
  transform: translateY(0);
}

.project-card:hover .project-image {
  transform: scale(1.015);
}

.project-card:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

@media (max-width: 768px) {
  .project-overlay {
    position: relative;
    padding: 24px 0 0;

    background: transparent;
    opacity: 1;
  }

  .project-info {
    transform: none;
  }

  .project-description {
    margin-bottom: 20px;
  }

  .project-bottom {
    flex-direction: column;
    gap: 8px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .project-image,
  .project-info,
  .project-overlay {
    transition: none;
  }

  .project-card:hover .project-image {
    transform: none;
  }
}

.cursor-label {
  position: fixed;
  z-index: 1000;

  padding: 9px 12px;

  background: var(--color-text);
  color: var(--color-background);

  font-size: 0.65rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;

  pointer-events: none;

  transform: translate(16px, 16px);
}

@media (hover: none), (pointer: coarse) {
  .cursor-label {
    display: none;
  }
}
</style>