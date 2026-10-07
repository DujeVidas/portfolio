<script setup lang="ts">
withDefaults(defineProps<{
  src: string
  alt: string
  caption?: string
  imageClass?: string
  objectFit?: 'cover' | 'contain'
}>(), {
  objectFit: 'cover'
})

const button = ref<HTMLButtonElement | null>(null)
const emit = defineEmits<{
  enlarge: [
    src: string,
    alt: string,
    caption: string | undefined,
    trigger: HTMLButtonElement | null
  ]
}>()

const hovering = ref(false)
const cursorX = ref(0)
const cursorY = ref(0)

function handleMouseMove(event: MouseEvent) {
  cursorX.value = event.clientX
  cursorY.value = event.clientY
}
</script>

<template>
  <button ref="button" class="enlargeable" :class="imageClass" type="button" :aria-label="`Enlarge ${alt}`"
    @click="emit('enlarge', src, alt, caption, button)" @mouseenter="hovering = true" @mouseleave="hovering = false"
    @mousemove="handleMouseMove">
    <img :src="src" :alt="alt" :style="{ objectFit }">

    <Teleport to="body">
      <div v-if="hovering" class="enlarge-cursor" :style="{
        left: `${cursorX}px`,
        top: `${cursorY}px`
      }" aria-hidden="true">
        Enlarge ↗
      </div>
    </Teleport>
  </button>
</template>

<style scoped>
.enlargeable {
  display: block;
  width: 100%;
  padding: 0;

  overflow: hidden;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}

.enlargeable img {
  display: block;

  width: 100%;
  height: 100%;

  object-fit: inherit;

  transition: transform var(--transition-normal);
}

.enlargeable:hover img {
  transform: scale(1.01);
}

.enlargeable:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

.enlarge-cursor {
  position: fixed;
  z-index: 1500;

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

@media (hover: none),
(pointer: coarse) {
  .enlarge-cursor {
    display: none;
  }
}

@media (prefers-reduced-motion: reduce) {
  .enlargeable img {
    transition: none;
  }

  .enlargeable:hover img {
    transform: none;
  }
}
</style>