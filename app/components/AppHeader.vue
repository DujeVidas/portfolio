<template>
  <header class="site-header">
    <div class="container header-inner">
      <NuxtLink to="/" class="site-name">
        Duje Vidas
      </NuxtLink>

      <nav class="navigation" aria-label="Main navigation">
        <NuxtLink to="/" class="nav-link">
          Work
        </NuxtLink>

        <NuxtLink to="/about" class="nav-link">
          About
        </NuxtLink>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.site-header {
  position: relative;
  z-index: 100;
  width: 100%;
  border-bottom: 1px solid var(--color-border);
}

.header-inner {
  min-height: 80px;

  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
}

.site-name,
.nav-link {
  font-size: 0.8rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.navigation {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-link {
  color: var(--color-text-muted);
  transition: color var(--transition-fast);
}

.nav-link:hover,
.nav-link:focus-visible,
.nav-link.router-link-active {
  color: var(--color-text);
}

.site-name:focus-visible,
.nav-link:focus-visible {
  outline: 1px solid var(--color-text);
  outline-offset: 6px;
}

@media (max-width: 768px) {
  .header-inner {
    min-height: 68px;
  }

  .navigation {
    gap: 20px;
  }
}
</style>