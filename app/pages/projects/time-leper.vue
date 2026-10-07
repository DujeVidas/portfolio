<script setup lang="ts">
type SculptDetail = 'head' | 'spine' | 'claws'

const activeSculptDetail = ref<SculptDetail>('head')

const sculptTechnicalOpen = ref(false)

const sculptDetails = {
  head: {
    number: '01',
    title: 'Head',
    image: '/images/time-leper/sculpt/head.png',
    description:
      'The head establishes the creature’s skeletal silhouette and distorted anatomy.'
  },
  spine: {
    number: '02',
    title: 'Spine',
    image: '/images/time-leper/sculpt/spine.png',
    description:
      'The spine became one of the creature’s defining features, with deep crevices, fractures and layered bone-like forms.'
  },
  claws: {
    number: '03',
    title: 'Claws',
    image: '/images/time-leper/sculpt/claws.png',
    description:
      'The extremities terminate in three elongated curved hooks, reinforcing the creature’s unnatural silhouette.'
  }
} satisfies Record<
  SculptDetail,
  {
    number: string
    title: string
    image: string
    description: string
  }
>

const activeDetail = computed(
  () => sculptDetails[activeSculptDetail.value]
)

type TextureView = 'baseColor' | 'roughness' | 'normal' | 'emission'

const activeTextureView = ref<TextureView>('baseColor')

const textureViews = {
  baseColor: {
    label: 'Base Color',
    image: '/images/time-leper/texturing/base-color.png',
    alt: 'Time Leper displaying the base color texture'
  },
  roughness: {
    label: 'Roughness',
    image: '/images/time-leper/texturing/roughness.png',
    alt: 'Time Leper displaying the roughness texture'
  },
  normal: {
    label: 'Normal',
    image: '/images/time-leper/texturing/normal.png',
    alt: 'Time Leper displaying the normal map'
  },
  emission: {
    label: 'Emission',
    image: '/images/time-leper/texturing/emission.png',
    alt: 'Time Leper displaying the emission mask'
  }
} satisfies Record<
  TextureView,
  {
    label: string
    image: string
    alt: string
  }
>

const activeTexture = computed(
  () => textureViews[activeTextureView.value]
)

function handleTextureTabKeydown(
  event: KeyboardEvent,
  currentKey: TextureView
) {
  const keys = Object.keys(textureViews) as TextureView[]
  const currentIndex = keys.indexOf(currentKey)

  let nextIndex = currentIndex

  switch (event.key) {
    case 'ArrowRight':
      nextIndex = (currentIndex + 1) % keys.length
      break

    case 'ArrowLeft':
      nextIndex = (currentIndex - 1 + keys.length) % keys.length
      break

    case 'Home':
      nextIndex = 0
      break

    case 'End':
      nextIndex = keys.length - 1
      break

    default:
      return
  }

  event.preventDefault()

  const nextKey = keys[nextIndex]

  if (!nextKey) {
    return
  }

  activeTextureView.value = nextKey

  nextTick(() => {
    document
      .getElementById(`texture-tab-${nextKey}`)
      ?.focus()
  })
}

const lightbox = reactive<{
  open: boolean
  src: string
  alt: string
  caption: string
  trigger: HTMLButtonElement | null
}>({
  open: false,
  src: '',
  alt: '',
  caption: '',
  trigger: null
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

</script>
<template>
  <main>
    <section class="project-hero">
      <div class="container hero-grid">
        <div class="hero-content">
          <p class="hero-label">
            Personal Project · 3D / Real-Time
          </p>

          <h1>
            Time Leper
          </h1>

          <p class="hero-type">
            Real-Time Creature
          </p>

          <p class="hero-description">
            A D&amp;D boss brought from a rough phone sketch through
            the complete 3D pipeline and into Unreal Engine 5.
          </p>

          <p class="hero-tools">
            Blender · Unreal Engine 5
          </p>
        </div>

        <div class="hero-visual">
          <img src="/images/time-leper/hero.png" alt="Final Time Leper creature in Unreal Engine 5">
        </div>
      </div>
    </section>
    <section class="origin">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            01 / Origin
          </p>

          <h2>
            From D&amp;D to 3D
          </h2>

          <p class="section-description">
            Time Leper began as a boss for my first D&amp;D 5e one-shot.
            Starting from a creature reference I found online, I made a rough
            sketch on my phone with my own changes before developing the
            design further in Blender.
          </p>
          <a class="character-sheet-link" href="/documents/sheet.pdf" target="_blank" rel="noopener noreferrer">
            View the D&amp;D 5e character sheet
            <span aria-hidden="true">↗</span>
          </a>
        </div>

        <div class="origin-grid">
          <figure class="origin-item">
            <EnlargeableImage src="/images/time-leper/origin/reference.jpg"
              alt="Visual reference used as inspiration for the Time Leper"
              caption="Pinterest Reference · Original artist unknown" image-class="origin-image" object-fit="contain"
              @enlarge="openLightbox" />

            <figcaption>
              <span>01</span>

              <span class="caption-content">
                <span class="caption-title">
                  Pinterest Reference
                </span>

                <span class="caption-credit">
                  Original artist unknown ·
                  <a href="https://www.pinterest.com/pin/876372408748492492/" target="_blank" rel="noopener noreferrer">
                    View source ↗
                  </a>
                </span>
              </span>
            </figcaption>
          </figure>

          <figure class="origin-item">
            <EnlargeableImage src="/images/time-leper/origin/sketch.jpg"
              alt="Original Time Leper concept sketch drawn on a phone" caption="Original Phone Sketch"
              image-class="origin-image" object-fit="contain" @enlarge="openLightbox" />

            <figcaption>
              <span>02</span>
              Phone Sketch
            </figcaption>
          </figure>

          <figure class="origin-item">
            <EnlargeableImage src="/images/time-leper/origin/sculpt.png" alt="High-poly Time Leper sculpt in Blender"
              caption="Blender Sculpt" image-class="origin-image" object-fit="contain" @enlarge="openLightbox" />

            <figcaption>
              <span>03</span>
              Blender Sculpt
            </figcaption>
          </figure>
        </div>
      </div>
    </section>
    <section id="overview" class="overview">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            02 / Overview
          </p>

          <h2>
            Project Overview
          </h2>

          <p class="section-description">
            What started as a creature for a D&amp;D one-shot became an
            exploration of the complete real-time 3D asset pipeline — from
            high-poly sculpting and retopology to texturing, baking, Unreal
            Engine materials, and Niagara effects.
          </p>
        </div>

        <dl class="project-specs">
          <div class="spec">
            <dt>Type</dt>
            <dd>Personal Project</dd>
          </div>

          <div class="spec">
            <dt>Role</dt>
            <dd>Solo</dd>
          </div>

          <div class="spec">
            <dt>Tools</dt>
            <dd>Blender · Unreal Engine 5</dd>
          </div>

          <div class="spec">
            <dt>Year</dt>
            <dd>2026</dd>
          </div>
        </dl>
      </div>
    </section>
    <section id="sculpt" class="sculpt">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            03 / Process
          </p>

          <h2>
            High-Poly Sculpt
          </h2>

          <p class="section-description">
            I developed the creature as a high-poly sculpt in Blender,
            focusing on its skeletal anatomy, elongated extremities and
            fractured bone-like surface detail.
          </p>
        </div>

        <div class="sculpt-explorer">
          <div class="sculpt-image">
            <img src="/images/time-leper/sculpt/full.png" alt="Full high-poly Time Leper sculpt in Blender">

            <button class="sculpt-hotspot hotspot-head" :class="{ active: activeSculptDetail === 'head' }" type="button"
              aria-label="View head sculpt detail" :aria-pressed="activeSculptDetail === 'head'"
              @click="activeSculptDetail = 'head'">
              <span>01</span>
              Head
            </button>

            <button class="sculpt-hotspot hotspot-spine" :class="{ active: activeSculptDetail === 'spine' }"
              type="button" aria-label="View spine sculpt detail" :aria-pressed="activeSculptDetail === 'spine'"
              @click="activeSculptDetail = 'spine'">
              <span>02</span>
              Spine
            </button>

            <button class="sculpt-hotspot hotspot-claws" :class="{ active: activeSculptDetail === 'claws' }"
              type="button" aria-label="View claw sculpt detail" :aria-pressed="activeSculptDetail === 'claws'"
              @click="activeSculptDetail = 'claws'">
              <span>03</span>
              Claws
            </button>
          </div>
          <p class="figure-caption">
            <span>FIG. 01</span>
            High-poly Time Leper sculpt
          </p>
          <div class="sculpt-detail">
            <div class="sculpt-detail-image">
              <img :src="activeDetail.image" :alt="`${activeDetail.title} detail of the Time Leper sculpt`">
            </div>

            <div class="sculpt-detail-content">
              <p class="detail-number">
                {{ activeDetail.number }}
              </p>

              <h3>
                {{ activeDetail.title }}
              </h3>

              <p>
                {{ activeDetail.description }}
              </p>
            </div>
          </div>
          <div class="technical-details">
            <button class="technical-toggle" type="button" :aria-expanded="sculptTechnicalOpen"
              aria-controls="sculpt-technical-content" @click="sculptTechnicalOpen = !sculptTechnicalOpen">
              <span>Technical details</span>

              <span class="technical-icon" :class="{ open: sculptTechnicalOpen }" aria-hidden="true">
                +
              </span>
            </button>

            <div v-show="sculptTechnicalOpen" id="sculpt-technical-content" class="technical-content">
              <div class="technical-grid">
                <div>
                  <p class="technical-label">
                    Multiresolution
                  </p>

                  <p>
                    I used Blender's Multiresolution modifier to keep the lower-resolution
                    game shell and high-resolution sculpt connected within the same
                    workflow. This allowed me to move between broad structural changes
                    and fine surface detailing without maintaining completely separate
                    sculpt files.
                  </p>
                </div>

                <div>
                  <p class="technical-label">
                    Surface Detail
                  </p>

                  <p>
                    Higher subdivision levels were used to sculpt the smaller crevices,
                    bone cracks and fractures that define the creature's calcified
                    surface.
                  </p>
                </div>

                <div>
                  <p class="technical-label">
                    Reshape
                  </p>

                  <p>
                    Blender's Reshape workflow was used to transfer sculpted detail back
                    into the Multiresolution hierarchy, preserving the high-resolution
                    forms while retaining the lighter base mesh underneath.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section id="retopology" class="retopology">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            04 / Process
          </p>

          <h2>
            Retopology
          </h2>

          <p class="section-description">
            The dense sculpt was rebuilt as a lighter game-ready mesh,
            preserving the creature's silhouette and major forms while
            producing geometry suitable for a real-time pipeline.
          </p>
        </div>

        <div class="retopology-comparison">
          <ImageComparison before-image="/images/time-leper/retopology/high-poly.png"
            after-image="/images/time-leper/retopology/low-poly.png" before-alt="High-poly Time Leper sculpt"
            after-alt="Game-ready Time Leper wireframe" before-label="High-Poly Clay"
            after-label="Game-Ready Wireframe" />

          <p class="figure-caption">
            <span>FIG. 02</span>
            High-poly sculpt compared with the game-ready topology
          </p>
        </div>
      </div>
    </section>
    <section id="uv" class="uv-section">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            05 / Process
          </p>

          <h2>
            UV Unwrapping
          </h2>

          <p class="section-description">
            I placed seams along less-visible areas of the creature before
            unwrapping and packing the mesh into a unified UV layout. The
            resulting islands were checked with Blender's stretch visualization
            before moving on to baking and texturing.
          </p>
        </div>

        <div class="uv-grid">
          <figure class="uv-item">
            <EnlargeableImage src="/images/time-leper/uv/seams.png"
              alt="UV seams marked on the Time Leper mesh in Blender" caption="UV Seams" image-class="uv-image"
              @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 03</span>
              Seams
            </figcaption>
          </figure>

          <figure class="uv-item">
            <EnlargeableImage src="/images/time-leper/uv/layout.png" alt="Packed Time Leper UV layout in Blender"
              caption="UV Layout" image-class="uv-image" object-fit="contain" @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 04</span>
              UV Layout
            </figcaption>
          </figure>

          <figure class="uv-item">
            <EnlargeableImage src="/images/time-leper/uv/stretch.png"
              alt="UV angle stretch visualization on the Time Leper mesh" caption="Angle Stretch" image-class="uv-image"
              object-fit="contain" @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 05</span>
              Angle Stretch
            </figcaption>
          </figure>
        </div>
      </div>
    </section>
    <section id="baking" class="baking-section">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            06 / Process
          </p>

          <h2>
            Normal Baking
          </h2>

          <p class="section-description">
            Detail from the high-poly sculpt was baked into a normal map and
            transferred onto the game-ready mesh. This preserves much of the
            sculpted surface detail without carrying the high-poly geometry
            into the final real-time asset.
          </p>
        </div>

        <div class="baking-grid">
          <figure class="baking-item">
            <EnlargeableImage src="/images/time-leper/baking/high-poly.png"
              alt="High-poly sculpt detail on the Time Leper spine" caption="High Poly" image-class="baking-image"
              @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 06</span>
              High Poly
            </figcaption>
          </figure>

          <figure class="baking-item">
            <EnlargeableImage src="/images/time-leper/baking/low-poly.png"
              alt="Raw game-ready Time Leper spine without the baked normal map" caption="Raw Low Poly"
              image-class="baking-image" @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 07</span>
              Raw Low Poly
            </figcaption>
          </figure>

          <figure class="baking-item">
            <EnlargeableImage src="/images/time-leper/baking/normal-baked.png"
              alt="Game-ready Time Leper spine with the baked normal map applied" caption="Normal Baked"
              image-class="baking-image" @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 08</span>
              Normal Baked
            </figcaption>
          </figure>
        </div>
      </div>
    </section>
    <section id="texturing" class="texturing-section">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            07 / Process
          </p>

          <h2>
            PBR Texturing
          </h2>

          <p class="section-description">
            The final surface combines color, roughness, baked normal detail
            and emissive elements to reinforce the creature's aged,
            bone-like appearance while remaining suitable for real-time rendering.
          </p>
        </div>

        <figure class="texturing-final">
          <EnlargeableImage src="/images/time-leper/texturing/final.png" alt="Final textured Time Leper"
            caption="Final PBR Material" image-class="texturing-final-image" @enlarge="openLightbox" />

          <figcaption class="figure-caption">
            <span>FIG. 09</span>
            Final PBR material
          </figcaption>
        </figure>

        <div class="texture-breakdown">
          <div class="texture-tabs" role="tablist" aria-label="Texture channels">
            <button v-for="(view, key) in textureViews" :id="`texture-tab-${key}`" :key="key" class="texture-tab"
              :class="{ active: activeTextureView === key }" type="button" role="tab"
              :aria-selected="activeTextureView === key" :aria-controls="`texture-panel-${key}`"
              :tabindex="activeTextureView === key ? 0 : -1" @click="activeTextureView = key as TextureView"
              @keydown="handleTextureTabKeydown($event, key as TextureView)">
              {{ view.label }}
            </button>
          </div>

          <div :id="`texture-panel-${activeTextureView}`" class="texture-viewer" role="tabpanel"
            :aria-labelledby="`texture-tab-${activeTextureView}`">
            <img :src="activeTexture.image" :alt="activeTexture.alt">
          </div>
        </div>
      </div>
    </section>
    <section id="unreal" class="unreal-section">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            08 / Unreal Engine
          </p>

          <h2>
            Material Setup
          </h2>

          <p class="section-description">
            Inside Unreal Engine 5, the baked textures were assembled into the
            final real-time material. The normal map was configured for Unreal's
            normal-map workflow, while the emissive eye mask was amplified to
            create the final glow.
          </p>
        </div>

        <div class="material-graph">
          <div class="material-graph-image">
            <img src="/images/time-leper/unreal/material-graph.png" alt="Time Leper material graph in Unreal Engine 5">

            <span class="graph-callout callout-base" type="button" aria-label="Base color material nodes">
              01
            </span>

            <span class="graph-callout callout-roughness" type="button" aria-label="Roughness material nodes">
              02
            </span>

            <span class="graph-callout callout-emission" type="button" aria-label="Emission material nodes">
              03
            </span>

            <span class="graph-callout callout-normal" type="button" aria-label="Normal map configuration">
              04
            </span>

          </div>

          <p class="figure-caption">
            <span>FIG. 10</span>
            Time Leper master material in Unreal Engine 5
          </p>
        </div>

        <div class="material-notes">
          <div>
            <span>01</span>
            <h3>Base Color</h3>
            <p>
              Supplies the creature's primary bone and surface coloration.
            </p>
          </div>

          <div>
            <span>02</span>
            <h3>Roughness</h3>
            <p>
              Controls the contrast between the dry bone surface and smoother,
              more reflective elements.
            </p>
          </div>

          <div>
            <span>03</span>
            <h3>Emission ×10</h3>
            <p>
              The eye emission mask is multiplied by a scalar value of 10 to
              produce a much stronger emissive glow and bloom response.
            </p>
          </div>

          <div>
            <span>04</span>
            <h3>Normal</h3>
            <p>
              The baked normal map was configured for Unreal's normal-map
              convention so the sculpted surface detail translated correctly.
            </p>
          </div>

        </div>
      </div>
    </section>
    <section id="niagara" class="niagara-section">
      <div class="container">
        <div class="section-intro">
          <p class="section-label">
            09 / Unreal Engine
          </p>

          <h2>
            Dark Aura
          </h2>

          <p class="section-description">
            To push the creature beyond the base asset, I built a dark smoke
            effect in Unreal Engine using a dedicated material and Niagara
            particle system. The effect surrounds the Time Leper with a shifting
            aura that reinforces its supernatural presence.
          </p>
        </div>

        <div class="aura-process">
          <figure class="aura-material">
            <EnlargeableImage src="/images/time-leper/niagara/smoke-material.png"
              alt="Smoke aura material setup in Unreal Engine 5" caption="Smoke Material" image-class="niagara-image"
              object-fit="contain" @enlarge="openLightbox" />

            <figcaption>
              <span>01</span>

              <div>
                <strong>Smoke Material</strong>

                <p>
                  A dedicated material defines the appearance and transparency
                  of the smoke used by the aura.
                </p>
              </div>
            </figcaption>
          </figure>

          <div class="aura-niagara">
            <span class="aura-step">
              02
            </span>

            <div>
              <h3>
                Niagara Distribution
              </h3>

              <p>
                In Niagara, the Time Leper's static mesh is used as the particle
                spawn surface, allowing the smoke to originate across the creature
                rather than from a single point.
              </p>
            </div>
          </div>
        </div>

        <figure class="aura-result">
          <div class="aura-result-image">
            <img src="/images/time-leper/niagara/final-aura.png"
              alt="Final Time Leper render with the dark Niagara smoke aura">
          </div>

          <figcaption class="figure-caption">
            <span>FIG. 11</span>
            Final dark aura in Unreal Engine 5
          </figcaption>
        </figure>
      </div>
    </section>
    <section id="final" class="final-section">
      <div class="container">
        <div class="final-heading">
          <p class="section-label">
            10 / Final
          </p>

          <h2>
            Final Presentation
          </h2>
        </div>

        <div class="final-gallery">
          <figure class="final-render final-render--hero">
            <EnlargeableImage src="/images/time-leper/final/render-01.png"
              alt="Final full-body Time Leper render in Blender" caption="Final Render" image-class="final-image"
              @enlarge="openLightbox" />

            <figcaption>
              <span>FIG. 12</span>
              Final Render
            </figcaption>
          </figure>

          <div class="final-gallery-secondary">
            <figure class="final-render">
              <EnlargeableImage src="/images/time-leper/final/render-02.png"
                alt="Alternate Time Leper render in Blender with a different pose and lighting" caption="Alternate View"
                image-class="final-image" @enlarge="openLightbox" />

              <figcaption>
                <span>FIG. 13</span>
                Alternate View
              </figcaption>
            </figure>

            <figure class="final-render">
              <EnlargeableImage src="/images/time-leper/final/render-03.png" alt="Time Leper in Unreal Engine 5"
                caption="Detail" image-class="final-image" @enlarge="openLightbox" />

              <figcaption>
                <span>FIG. 14</span>
                Detail
              </figcaption>
            </figure>
          </div>
        </div>
      </div>
    </section>
    <section class="project-end">
      <div class="container">
        <NuxtLink to="/" class="back-to-work">
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
    <ImageLightbox :open="lightbox.open" :src="lightbox.src" :alt="lightbox.alt" :caption="lightbox.caption"
      @close="closeLightbox" />
  </main>
</template>

<style scoped>
.project-hero {
  min-height: calc(100vh - 81px);

  display: flex;
  align-items: center;

  padding-block: 72px 96px;
}

.hero-grid {
  display: grid;
  grid-template-columns: minmax(0, 0.8fr) minmax(0, 1.2fr);
  align-items: center;
  gap: clamp(48px, 7vw, 120px);
}

.hero-content {
  max-width: 560px;
}

.hero-label {
  margin: 0 0 28px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

h1 {
  margin: 0;

  font-size: clamp(4rem, 7vw, 8rem);
  font-weight: 500;
  line-height: 0.88;
  letter-spacing: -0.055em;

  text-transform: uppercase;
}

.hero-type {
  margin: 24px 0 0;

  font-size: 1rem;
  font-weight: 500;
}

.hero-description {
  max-width: 470px;
  margin: 32px 0 0;

  color: var(--color-text-muted);

  font-size: clamp(1rem, 1.2vw, 1.15rem);
  line-height: 1.7;
}

.hero-tools {
  margin: 40px 0 0;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.hero-visual {
  overflow: hidden;
  background: var(--color-surface);
}

.hero-visual img {
  width: 100%;
  height: auto;
  object-fit: cover;
}

@media (max-width: 900px) {
  .project-hero {
    min-height: auto;
    padding-block: 72px;
  }

  .hero-grid {
    grid-template-columns: 1fr;
    gap: 56px;
  }

  .hero-content {
    max-width: 650px;
  }

  h1 {
    font-size: clamp(4rem, 17vw, 7rem);
  }
}

@media (max-width: 480px) {
  .project-hero {
    padding-block: 56px;
  }

  h1 {
    font-size: clamp(3.5rem, 18vw, 5rem);
  }

  .hero-description {
    margin-top: 24px;
  }

  .hero-tools {
    margin-top: 32px;
  }
}

.origin {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.section-intro {
  max-width: 850px;
  margin-bottom: 72px;
}

.section-label {
  margin: 0 0 24px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.section-intro h2 {
  margin: 0;

  font-size: clamp(2.8rem, 5vw, 5.5rem);
  font-weight: 500;
  line-height: 1;
  letter-spacing: -0.045em;
}

.section-description {
  max-width: 650px;
  margin: 32px 0 0;

  color: var(--color-text-muted);

  font-size: 1rem;
  line-height: 1.7;
}

.origin-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
}

.origin-item {
  min-width: 0;
  margin: 0;
}

.origin-image {
  display: block;
  width: 100%;
  padding: 0;

  overflow: hidden;
  aspect-ratio: 4 / 5;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}



.origin-item figcaption {
  display: flex;
  gap: 12px;

  margin-top: 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.origin-item figcaption span {
  color: var(--color-text);
}

@media (max-width: 768px) {
  .origin {
    padding-block: 96px;
  }

  .section-intro {
    margin-bottom: 48px;
  }

  .origin-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .origin-image {
    aspect-ratio: auto;
  }

}

.caption-content {
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.caption-title {
  color: var(--color-text-muted);
}

.caption-credit {
  color: #666;
  font-size: 0.62rem;
  letter-spacing: 0.04em;
  text-transform: none;
}

.caption-credit a {
  color: var(--color-text-muted);
  transition: color var(--transition-fast);
}

.caption-credit a:hover,
.caption-credit a:focus-visible {
  color: var(--color-text);
}

.overview {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.project-specs {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));

  margin: 0;
  padding: 0;

  border-top: 1px solid var(--color-border);
  border-bottom: 1px solid var(--color-border);
}

.spec {
  min-width: 0;
  padding: 28px 24px 32px 0;
}

.spec+.spec {
  padding-left: 24px;
  border-left: 1px solid var(--color-border);
}

.spec dt {
  margin-bottom: 14px;

  color: var(--color-text-muted);

  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.spec dd {
  margin: 0;

  font-size: clamp(0.95rem, 1.2vw, 1.1rem);
  line-height: 1.5;
}

@media (max-width: 768px) {
  .overview {
    padding-block: 96px;
  }

  .project-specs {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .spec {
    padding: 24px 20px 24px 0;
  }

  .spec+.spec {
    padding-left: 20px;
  }

  .spec:nth-child(3) {
    padding-left: 0;
    border-left: 0;
    border-top: 1px solid var(--color-border);
  }

  .spec:nth-child(4) {
    border-top: 1px solid var(--color-border);
  }
}

@media (max-width: 480px) {
  .project-specs {
    grid-template-columns: 1fr;
  }

  .spec,
  .spec+.spec,
  .spec:nth-child(3) {
    padding: 22px 0;
    border-left: 0;
  }

  .spec+.spec {
    border-top: 1px solid var(--color-border);
  }
}

.character-sheet-link {
  display: inline-flex;
  align-items: center;
  gap: 8px;

  margin-top: 24px;

  color: var(--color-text);

  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.06em;
  text-transform: uppercase;

  border-bottom: 1px solid var(--color-border);

  transition: border-color var(--transition-fast);
}

.character-sheet-link:hover,
.character-sheet-link:focus-visible {
  border-color: var(--color-text);
}

.character-sheet-link:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

.sculpt {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.sculpt-explorer {
  margin-top: 72px;
}

.sculpt-image {
  position: relative;

  width: 100%;
  overflow: hidden;

  background: var(--color-surface);
}

.sculpt-image img {
  display: block;
  width: 100%;
  height: auto;
}

.figure-caption {
  display: flex;
  gap: 12px;

  margin: 14px 0 0;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.figure-caption span {
  color: var(--color-text);
}

@media (max-width: 768px) {
  .sculpt {
    padding-block: 96px;
  }

  .sculpt-explorer {
    margin-top: 48px;
  }

  .sculpt-detail {
    grid-template-columns: 1fr;
    gap: 28px;
    margin-top: 48px;
  }

  .sculpt-detail-content {
    max-width: 600px;
  }
}

.sculpt-hotspot {
  position: absolute;

  display: flex;
  align-items: center;
  gap: 8px;

  padding: 9px 12px;

  border: 1px solid rgba(255, 255, 255, 0.35);
  background: rgba(10, 10, 10, 0.8);
  color: var(--color-text);

  font-size: 0.65rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;

  cursor: pointer;
  backdrop-filter: blur(8px);

  transform: translate(-50%, -50%);

  transition:
    background var(--transition-fast),
    color var(--transition-fast),
    border-color var(--transition-fast);
}

.sculpt-hotspot span {
  color: var(--color-text-muted);
}

.sculpt-hotspot:hover,
.sculpt-hotspot.active {
  background: var(--color-text);
  color: var(--color-background);
  border-color: var(--color-text);
}

.sculpt-hotspot.active span,
.sculpt-hotspot:hover span {
  color: var(--color-background);
}

.sculpt-hotspot:focus-visible {
  outline: 2px solid var(--color-text);
  outline-offset: 4px;
}

.hotspot-head {
  left: 45%;
  top: 10%;
}

.hotspot-spine {
  left: 43%;
  top: 40%;
}

.hotspot-claws {
  left: 85%;
  top: 33%;
}

.sculpt-detail {
  display: grid;
  grid-template-columns: minmax(0, 1.5fr) minmax(280px, 0.5fr);
  gap: clamp(40px, 6vw, 96px);
  align-items: center;

  margin-top: 72px;
}

.sculpt-detail-image {
  overflow: hidden;
  background: var(--color-surface);
}

.sculpt-detail-image img {
  display: block;
  width: 100%;
  height: auto;
}

.sculpt-detail-content {
  max-width: 420px;
}

.detail-number {
  margin: 0 0 18px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.1em;
}

.sculpt-detail-content h3 {
  margin: 0;

  font-size: clamp(2rem, 4vw, 4rem);
  font-weight: 500;
  letter-spacing: -0.04em;
}

.sculpt-detail-content>p:last-child {
  margin: 24px 0 0;

  color: var(--color-text-muted);

  line-height: 1.7;
}

.technical-details {
  margin-top: 96px;
  border-top: 1px solid var(--color-border);
  border-bottom: 1px solid var(--color-border);
}

.technical-toggle {
  display: flex;
  align-items: center;
  justify-content: space-between;

  width: 100%;
  padding: 24px 0;

  border: 0;
  background: transparent;
  color: var(--color-text);

  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-align: left;
  text-transform: uppercase;

  cursor: pointer;
}

.technical-icon {
  color: var(--color-text-muted);

  font-size: 1.2rem;
  font-weight: 300;

  transition: transform var(--transition-fast);
}

.technical-icon.open {
  transform: rotate(45deg);
}

.technical-toggle:hover .technical-icon {
  color: var(--color-text);
}

.technical-toggle:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

.technical-content {
  padding: 16px 0 48px;
}

.technical-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: clamp(32px, 5vw, 80px);
}

.technical-label {
  margin: 0 0 14px;

  color: var(--color-text);

  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.technical-grid>div>p:last-child {
  margin: 0;

  color: var(--color-text-muted);

  font-size: 0.9rem;
  line-height: 1.7;
}

@media (max-width: 768px) {
  .technical-details {
    margin-top: 64px;
  }

  .technical-grid {
    grid-template-columns: 1fr;
    gap: 36px;
  }
}

.retopology {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.retopology-comparison {
  margin-top: 72px;
}

@media (max-width: 768px) {
  .retopology {
    padding-block: 96px;
  }

  .retopology-comparison {
    margin-top: 48px;
  }
}

.uv-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.uv-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;

  margin-top: 72px;
}

.uv-item {
  min-width: 0;
  margin: 0;
}

.uv-image {
  display: block;

  width: 100%;
  padding: 0;

  overflow: hidden;
  aspect-ratio: 4 / 3;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}

.uv-item figcaption {
  display: flex;
  gap: 12px;

  margin-top: 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.uv-item figcaption span {
  color: var(--color-text);
}

@media (max-width: 768px) {
  .uv-section {
    padding-block: 96px;
  }

  .uv-grid {
    grid-template-columns: 1fr;
    gap: 48px;

    margin-top: 48px;
  }

  .uv-image {
    aspect-ratio: auto;
  }
}

.baking-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.baking-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;

  margin-top: 72px;
}

.baking-item {
  min-width: 0;
  margin: 0;
}

.baking-image {
  display: block;

  width: 100%;
  padding: 0;

  overflow: hidden;
  aspect-ratio: 1 / 1;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}

.baking-item figcaption {
  display: flex;
  gap: 12px;

  margin-top: 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.baking-item figcaption span {
  color: var(--color-text);
}

@media (max-width: 768px) {
  .baking-section {
    padding-block: 96px;
  }

  .baking-grid {
    grid-template-columns: 1fr;
    gap: 48px;

    margin-top: 48px;
  }
}

.texturing-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.texturing-final {
  margin: 72px 0 0;
}

.texturing-final-image {
  display: block;
  width: 100%;
  padding: 0;

  overflow: hidden;

  border: 0;
  background: var(--color-surface);
  cursor: pointer;
}

.texture-breakdown {
  margin-top: 96px;
}

.texture-tabs {
  display: flex;
  flex-wrap: wrap;

  border-top: 1px solid var(--color-border);
  border-bottom: 1px solid var(--color-border);
}

.texture-tab {
  padding: 18px 24px;

  border: 0;
  border-right: 1px solid var(--color-border);

  background: transparent;
  color: var(--color-text-muted);

  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;

  cursor: pointer;

  transition:
    background var(--transition-fast),
    color var(--transition-fast);
}

.texture-tab:hover,
.texture-tab.active {
  background: var(--color-text);
  color: var(--color-background);
}

.texture-tab:focus-visible {
  position: relative;
  z-index: 1;

  outline: 1px solid var(--color-text);
  outline-offset: 4px;
}

.texture-viewer {
  margin-top: 32px;
  overflow: hidden;

  background: var(--color-surface);
}

.texture-viewer img {
  display: block;

  width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  .texturing-section {
    padding-block: 96px;
  }

  .texturing-final {
    margin-top: 48px;
  }

  .texture-breakdown {
    margin-top: 64px;
  }

  .texture-tabs {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  .texture-tab {
    border-bottom: 1px solid var(--color-border);
  }

  .texture-viewer {
    margin-top: 24px;
  }
}

.unreal-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.material-graph {
  margin-top: 72px;
}

.material-graph-image {
  position: relative;
  overflow: hidden;

  background: var(--color-surface);
}

.material-graph-image>img {
  display: block;
  width: 100%;
  height: auto;
}

.graph-callout {
  position: absolute;

  display: grid;
  place-items: center;

  width: 36px;
  height: 36px;

  border: 1px solid var(--color-text);
  border-radius: 50%;

  background: var(--color-background);
  color: var(--color-text);

  font-size: 0.65rem;
  font-weight: 600;

  transform: translate(-50%, -50%);
  pointer-events: none;
}

.callout-base {
  left: 22%;
  top: 10%;
}

.callout-roughness {
  left: 22%;
  top: 32%;
}

.callout-emission {
  left: 22%;
  top: 60%;
}

.callout-normal {
  left: 22%;
  top: 75%;
}

.material-notes {
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 1px;

  margin-top: 72px;

  background: var(--color-border);
  border: 1px solid var(--color-border);
}

.material-notes>div {
  padding: 28px;
  background: var(--color-background);
}

.material-notes span {
  color: var(--color-text-muted);

  font-size: 0.65rem;
  letter-spacing: 0.1em;
}

.material-notes h3 {
  margin: 18px 0 0;

  font-size: 1rem;
  font-weight: 500;
}

.material-notes p {
  margin: 16px 0 0;

  color: var(--color-text-muted);

  font-size: 0.85rem;
  line-height: 1.7;
}

@media (max-width: 900px) {
  .material-notes {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .unreal-section {
    padding-block: 96px;
  }

  .material-graph {
    margin-top: 48px;
  }

  .graph-callout {
    width: 30px;
    height: 30px;
  }

  .material-notes {
    margin-top: 48px;
  }
}

@media (max-width: 520px) {
  .material-notes {
    grid-template-columns: 1fr;
  }
}

.niagara-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.aura-process {
  display: grid;
  grid-template-columns:
    minmax(0, 1.4fr) minmax(280px, 0.6fr);

  gap: clamp(48px, 7vw, 120px);
  align-items: center;

  margin-top: 72px;
}

.aura-material {
  min-width: 0;
  margin: 0;
}

.niagara-image {
  display: block;

  width: 100%;
  padding: 0;

  overflow: hidden;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}

.aura-material figcaption {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 16px;

  margin-top: 18px;
}

.aura-material figcaption>span,
.aura-step {
  color: var(--color-text-muted);

  font-size: 0.65rem;
  letter-spacing: 0.1em;
}

.aura-material strong {
  display: block;

  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.aura-material figcaption p {
  max-width: 500px;
  margin: 10px 0 0;

  color: var(--color-text-muted);

  font-size: 0.85rem;
  line-height: 1.6;
}

.aura-niagara {
  display: grid;
  grid-template-columns: auto 1fr;
  gap: 20px;

  padding-top: 24px;

  border-top: 1px solid var(--color-border);
}

.aura-niagara h3 {
  margin: 0;

  font-size: 1rem;
  font-weight: 500;
  letter-spacing: 0.04em;
  text-transform: uppercase;
}

.aura-niagara p {
  margin: 16px 0 0;

  color: var(--color-text-muted);

  font-size: 0.9rem;
  line-height: 1.7;
}

.aura-result {
  margin: 120px 0 0;
}

.aura-result-image {
  overflow: hidden;

  background: var(--color-surface);
}

.aura-result-image img {
  display: block;

  width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  .niagara-section {
    padding-block: 96px;
  }

  .aura-process {
    grid-template-columns: 1fr;
    gap: 56px;

    margin-top: 48px;
  }

  .aura-result {
    margin-top: 80px;
  }
}

.final-section {
  padding-block: 160px;
  border-top: 1px solid var(--color-border);
}

.final-heading {
  margin-bottom: 72px;
}

.final-heading h2 {
  margin: 0;

  font-size: clamp(2.8rem, 5vw, 5.5rem);
  font-weight: 500;
  line-height: 1;
  letter-spacing: -0.045em;
}

.final-gallery {
  display: flex;
  flex-direction: column;
  gap: 96px;
}

.final-render {
  min-width: 0;
  margin: 0;
}

.final-image {
  display: block;

  width: 100%;
  padding: 0;

  overflow: hidden;

  border: 0;
  background: var(--color-surface);

  cursor: pointer;
}

.final-render figcaption {
  display: flex;
  gap: 12px;

  margin-top: 14px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.final-render figcaption span {
  color: var(--color-text);
}


.final-gallery-secondary {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 24px;
}


@media (max-width: 768px) {
  .final-section {
    padding-block: 96px;
  }

  .final-heading {
    margin-bottom: 48px;
  }

  .final-gallery {
    gap: 56px;
  }

  .final-gallery-secondary {
    grid-template-columns: 1fr;
    gap: 48px;
  }
}

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

  transition: color var(--transition-fast);
}

.back-title>span {
  flex-shrink: 0;

  color: var(--color-text-muted);

  font-size: 0.45em;

  transition:
    color var(--transition-fast),
    transform var(--transition-fast);
}

.back-to-work:hover .back-title>span {
  color: var(--color-text);
  transform: translate(6px, -6px);
}

.back-to-work:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 8px;
}

@media (max-width: 768px) {
  .project-end {
    padding-block: 80px;
  }

  .back-to-work {
    gap: 18px;
  }

  .back-title {
    font-size: clamp(2.7rem, 13vw, 5rem);
  }
}

@media (prefers-reduced-motion: reduce) {
  .back-title>span {
    transition: none;
  }

  .back-to-work:hover .back-title>span {
    transform: none;
  }
}
</style>