<template>
  <footer class="site-footer">
    <div class="container footer-inner">
      <div class="footer-contact">
        <p class="footer-name">
          Duje Vidas
        </p>

        <div class="footer-links">
          <a href="mailto:duje.vidas.dev@gmail.com">
            Email
          </a>

          <a
            href="https://www.linkedin.com/in/duje-vidas"
            target="_blank"
            rel="noopener noreferrer"
          >
            LinkedIn
          </a>

          <a
            href="https://github.com/dujevidas"
            target="_blank"
            rel="noopener noreferrer"
          >
            GitHub
          </a>
        </div>
      </div>

      <div class="footer-meta">
        <p>
          Designed & developed by Duje Vidas
        </p>

        <p>
          Nuxt · Vue · TypeScript
        </p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  border-top: 1px solid var(--color-border);
}

.footer-inner {
  display: flex;
  justify-content: space-between;
  gap: 64px;

  padding-block: 56px;
}

.footer-name {
  margin: 0 0 16px;

  font-size: 0.75rem;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.footer-links {
  display: flex;
  gap: 24px;
}

.footer-links a,
.footer-meta {
  color: var(--color-text-muted);
  font-size: 0.75rem;
}

.footer-links a {
  transition: color var(--transition-fast);
}

.footer-links a:hover,
.footer-links a:focus-visible {
  color: var(--color-text);
}

.footer-links a:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 5px;
}

.footer-meta {
  text-align: right;
  line-height: 1.6;
}

.footer-meta p {
  margin: 0;
}

@media (max-width: 768px) {
  .footer-inner {
    flex-direction: column;
    gap: 40px;

    padding-block: 40px;
  }

  .footer-meta {
    text-align: left;
  }
}
</style>