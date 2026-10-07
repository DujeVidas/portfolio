<script setup lang="ts">
const props = withDefaults(defineProps<{
  beforeImage: string
  afterImage: string
  beforeAlt: string
  afterAlt: string
  beforeLabel?: string
  afterLabel?: string
}>(), {
  beforeLabel: 'Before',
  afterLabel: 'After'
})

const position = ref(50)

function updatePosition(event: Event) {
  const target = event.target as HTMLInputElement
  position.value = Number(target.value)
}
</script>

<template>
  <div class="comparison">
    <div class="comparison-images">
      <img :src="props.beforeImage" :alt="props.beforeAlt" class="comparison-image comparison-before">

      <img :src="props.afterImage" :alt="props.afterAlt" class="comparison-image comparison-after" :style="{
        clipPath: `inset(0 0 0 ${position}%)`
      }">

      <div class="comparison-divider" :style="{ left: `${position}%` }" aria-hidden="true">
        <span class="comparison-handle">
          ↔
        </span>
      </div>

      <span class="comparison-label label-before">
        {{ props.beforeLabel }}
      </span>

      <span class="comparison-label label-after">
        {{ props.afterLabel }}
      </span>

      <input class="comparison-range" type="range" min="0" max="100" :value="position"
        :aria-label="`Compare ${props.beforeLabel} and ${props.afterLabel}`" @input="updatePosition">
    </div>
  </div>
</template>

<style scoped>
.comparison {
  width: 100%;
}

.comparison-images {
  position: relative;
  overflow: hidden;

  width: 100%;
  aspect-ratio: 1351 / 957;

  background: var(--color-surface);
}

.comparison-image {
  position: absolute;
  inset: 0;

  display: block;

  width: 100%;
  height: 100%;

  object-fit: contain;
}


.comparison-before {
  z-index: 1;
}



.comparison-after {
  z-index: 2;
}

.comparison-divider {
  position: absolute;
  z-index: 3;

  top: 0;
  bottom: 0;

  width: 1px;

  background: rgba(255, 255, 255, 0.8);

  transform: translateX(-50%);
  pointer-events: none;
}

.comparison-handle {
  position: absolute;
  top: 50%;
  left: 50%;

  display: grid;
  place-items: center;

  width: 44px;
  height: 44px;

  border: 1px solid var(--color-text);
  border-radius: 50%;

  background: var(--color-background);
  color: var(--color-text);

  font-size: 0.85rem;

  transform: translate(-50%, -50%);
}

.comparison-label {
  position: absolute;
  z-index: 4;

  top: 20px;

  padding: 8px 10px;

  background: rgba(10, 10, 10, 0.75);
  color: var(--color-text);

  font-size: 0.62rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;

  pointer-events: none;
  backdrop-filter: blur(6px);
}

.label-before {
  left: 20px;
}

.label-after {
  right: 20px;
}

.comparison-range {
  position: absolute;
  z-index: 5;
  inset: 0;

  width: 100%;
  height: 100%;
  margin: 0;

  opacity: 0;
  cursor: ew-resize;
}

.comparison-range:focus-visible {
  opacity: 1;

  height: 4px;
  top: 50%;

  accent-color: white;

  transform: translateY(-50%);
}

@media (max-width: 768px) {

  .comparison-label {
    top: 12px;
  }

  .label-before {
    left: 12px;
  }

  .label-after {
    right: 12px;
  }

  .comparison-handle {
    width: 40px;
    height: 40px;
  }
}
</style>