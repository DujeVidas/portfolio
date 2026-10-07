<script setup lang="ts">
const props = defineProps<{
  open: boolean
  src: string
  alt: string
  caption?: string
}>()

const emit = defineEmits<{
  close: []
}>()

const dialog = ref<HTMLDivElement | null>(null)

const closeButton = ref<HTMLButtonElement | null>(null)

function close() {
  emit('close')
}

function handleKeydown(event: KeyboardEvent) {
  if (!props.open) {
    return
  }

  if (event.key === 'Escape') {
    event.preventDefault()
    close()
    return
  }

  if (event.key === 'Tab') {
    event.preventDefault()
    closeButton.value?.focus()
  }
}

watch(
  () => props.open,
  async (open) => {
    if (import.meta.client) {
      document.body.style.overflow = open ? 'hidden' : ''
    }

    if (open) {
      await nextTick()
      closeButton.value?.focus()
    }
  }
)

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)
})

onBeforeUnmount(() => {
  window.removeEventListener('keydown', handleKeydown)

  if (import.meta.client) {
    document.body.style.overflow = ''
  }
})
</script>

<template>
  <Teleport to="body">
    <Transition name="lightbox">
      <div ref="dialog" v-if="open" class="lightbox" role="dialog" aria-modal="true" :aria-label="caption || alt"
        @click.self="close">
        <button ref="closeButton" class="lightbox-close" type="button" aria-label="Close image" @click="close">
          Close ×
        </button>

        <div class="lightbox-content">
          <img :src="src" :alt="alt">

          <p v-if="caption" class="lightbox-caption">
            {{ caption }}
          </p>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<style scoped>
.lightbox {
  position: fixed;
  z-index: 2000;
  inset: 0;

  display: grid;
  place-items: center;

  padding: 72px clamp(20px, 4vw, 64px) 40px;

  background: rgba(5, 5, 5, 0.96);
}

.lightbox-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;

  max-width: 100%;
  max-height: 100%;
}

.lightbox-content img {
  display: block;

  max-width: 100%;
  max-height: calc(100vh - 150px);

  width: auto;
  height: auto;

  object-fit: contain;
}

.lightbox-caption {
  margin: 0;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-align: center;
  text-transform: uppercase;
}

.lightbox-close {
  position: absolute;
  top: 24px;
  right: clamp(20px, 4vw, 64px);

  padding: 8px 0;

  border: 0;
  background: transparent;
  color: var(--color-text);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;

  cursor: pointer;
}

.lightbox-close:hover {
  color: var(--color-text-muted);
}

.lightbox-close:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

.lightbox-enter-active,
.lightbox-leave-active {
  transition: opacity var(--transition-fast);
}

.lightbox-enter-from,
.lightbox-leave-to {
  opacity: 0;
}

@media (prefers-reduced-motion: reduce) {

  .lightbox-enter-active,
  .lightbox-leave-active {
    transition: none;
  }
}
</style>