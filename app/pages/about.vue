<template>
  <main>
    <section class="about-hero">
        <div class="container">
            <p class="about-label">
            About
            </p>

            <h1>
            Software developer interested in backend systems,
            automation, and the space between code and graphics.
            </h1>
        </div>
    </section>

    <section class="about-intro">
      <div class="container about-intro-grid">
        <p class="about-index">
          01 / Introduction
        </p>

        <div class="about-copy">
            <p class="about-lead">
                I'm a University Master of Informatics focused on software development,
                with a particular interest in backend technologies.
            </p>

            <p>
                My experience spans backend and web development, databases,
                containerization, computer vision, and automation. During my software
                development internship, I worked on a full-stack VR Tour Management
                Platform involving REST APIs, PostgreSQL, Prisma ORM, authentication,
                Docker, and application deployment.
            </p>

            <p>
                My Master's thesis brought software development and 3D together. I built
                an automated synthetic dataset generation system using Blender and Python,
                with procedural scene generation, domain randomization, automatic data
                annotation, and the training and evaluation of YOLO computer vision models.
            </p>

            <p>
                Outside of purely software-focused work, I enjoy experimenting with 3D
                and real-time graphics. Whether I'm building a backend system, automating
                a workflow, or creating something in Blender, I'm most interested in
                understanding the technical problem and turning it into a practical,
                finished solution.
            </p>
        </div>
      </div>
    </section>

    <section class="about-details">
      <div class="container">
        <div class="details-grid">
            <div class="detail-column">
                <p class="detail-label">
                Development
                </p>

                <ul>
                <li>Python</li>
                <li>TypeScript / JavaScript</li>
                <li>Node.js / Express.js</li>
                <li>REST APIs</li>
                <li>Git / Linux</li>
                </ul>
            </div>

            <div class="detail-column">
                <p class="detail-label">
                Data / Infrastructure
                </p>

                <ul>
                <li>PostgreSQL / MySQL</li>
                <li>Redis</li>
                <li>Prisma ORM</li>
                <li>Docker</li>
                <li>Computer Vision / YOLO</li>
                </ul>
            </div>

            <div class="detail-column">
                <p class="detail-label">
                Graphics / Automation
                </p>

                <ul>
                <li>Blender</li>
                <li>Unreal Engine 5</li>
                <li>Procedural Generation</li>
                <li>Synthetic Data</li>
                <li>Python Automation</li>
                </ul>
            </div>
        </div>
      </div>
    </section>

    <section class="about-contact">
      <div class="container">
        <p class="about-label">
          02 / Contact
        </p>

        <div class="contact-heading">
          <h2>
            Let's talk.
          </h2>

          <p>
            For work, collaboration, or just to say hello.
          </p>
        </div>

        <div class="contact-links">
          <a href="mailto:dujevidas@gmail.com">
            <span>Email</span>
            <span aria-hidden="true">↗</span>
          </a>

          <a
            href="https://github.com/dujevidas"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span>GitHub</span>
            <span aria-hidden="true">↗</span>
          </a>

          <a
            href="https://www.linkedin.com/in/dujevidas/"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span>LinkedIn</span>
            <span aria-hidden="true">↗</span>
          </a>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.about-hero {
  display: flex;
  align-items: flex-end;

  min-height: 70vh;
  padding-block: 96px 120px;
}

.about-label {
  margin: 0 0 28px;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.about-hero h1 {
  max-width: 1150px;
  margin: 0;

  font-size: clamp(3.5rem, 7vw, 8rem);
  font-weight: 500;
  line-height: 0.94;
  letter-spacing: -0.055em;
}

.about-intro {
  padding-block: 160px;

  border-top: 1px solid var(--color-border);
}

.about-intro-grid {
  display: grid;
  grid-template-columns: minmax(160px, 0.35fr) minmax(0, 1fr);
  gap: clamp(48px, 9vw, 160px);
}

.about-index {
  margin: 6px 0 0;

  color: var(--color-text-muted);

  font-size: 0.7rem;
  font-weight: 500;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

.about-copy {
  max-width: 780px;
}

.about-copy p {
  margin: 0;

  color: var(--color-text-muted);

  font-size: clamp(1rem, 1.3vw, 1.15rem);
  line-height: 1.8;
}

.about-copy p + p {
  margin-top: 32px;
}

.about-copy .about-lead {
  margin-bottom: 56px;

  color: var(--color-text);

  font-size: clamp(1.8rem, 3vw, 3.2rem);
  font-weight: 400;
  line-height: 1.25;
  letter-spacing: -0.03em;
}

.about-details {
  padding-block: 120px;

  border-top: 1px solid var(--color-border);
}

.details-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1px;

  border: 1px solid var(--color-border);
  background: var(--color-border);
}

.detail-column {
  padding: 32px;

  background: var(--color-background);
}

.detail-label {
  margin: 0 0 40px;

  color: var(--color-text-muted);

  font-size: 0.68rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.detail-column ul {
  display: flex;
  flex-direction: column;
  gap: 12px;

  margin: 0;
  padding: 0;

  list-style: none;
}

.detail-column li,
.detail-text {
  margin: 0;

  font-size: 0.95rem;
  line-height: 1.6;
}

.detail-text {
  max-width: 320px;

  color: var(--color-text-muted);
}

.about-contact {
  padding-block: 160px;

  border-top: 1px solid var(--color-border);
}

.contact-heading {
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(220px, 0.35fr);
  gap: 64px;
  align-items: end;

  margin-bottom: 96px;
}

.contact-heading h2 {
  margin: 0;

  font-size: clamp(4rem, 9vw, 9rem);
  font-weight: 500;
  line-height: 0.9;
  letter-spacing: -0.055em;
}

.contact-heading p {
  margin: 0;

  color: var(--color-text-muted);

  font-size: 0.9rem;
  line-height: 1.7;
}

.contact-links {
  border-top: 1px solid var(--color-border);
}

.contact-links a {
  display: flex;
  align-items: center;
  justify-content: space-between;

  padding-block: 24px;

  border-bottom: 1px solid var(--color-border);

  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.contact-links a span:last-child {
  color: var(--color-text-muted);

  transition:
    color var(--transition-fast),
    transform var(--transition-fast);
}

.contact-links a:hover span:last-child {
  color: var(--color-text);
  transform: translate(5px, -5px);
}

.contact-links a:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

@media (max-width: 768px) {
  .about-hero {
    min-height: 62vh;
    padding-block: 64px 80px;
  }

  .about-hero h1 {
    font-size: clamp(3rem, 14vw, 5rem);
  }

  .about-intro {
    padding-block: 96px;
  }

  .about-intro-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .about-copy .about-lead {
    margin-bottom: 40px;
  }

  .about-details {
    padding-block: 80px;
  }

  .details-grid {
    grid-template-columns: 1fr;
  }

  .detail-label {
    margin-bottom: 28px;
  }

  .about-contact {
    padding-block: 96px;
  }

  .contact-heading {
    grid-template-columns: 1fr;
    gap: 32px;

    margin-bottom: 64px;
  }

  .contact-heading h2 {
    font-size: clamp(4rem, 20vw, 7rem);
  }
}

@media (prefers-reduced-motion: reduce) {
  .contact-links a span:last-child {
    transition: none;
  }

  .contact-links a:hover span:last-child {
    transform: none;
  }
}
</style>