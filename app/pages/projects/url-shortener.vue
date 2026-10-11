<template>
    <main class="project-page">
        <section class="project-hero">
            <div class="hero-top">
                <NuxtLink to="/" class="back-link">
                    <span>←</span> Back to all work
                </NuxtLink>

                <span class="project-index">
                    BACKEND ENGINEERING / 2026
                </span>
            </div>

            <div class="hero-content">
                <div class="hero-copy">
                    <p class="eyebrow">
                        Personal Project · Backend Development
                    </p>

                    <h1>
                        URL Shortener
                        <span>& Analytics API</span>
                    </h1>

                    <p class="hero-description">
                        A production-style REST API for shortening URLs,
                        tracking click analytics, and securely managing links.
                        Built with FastAPI, PostgreSQL, and Redis, with a focus
                        on security, caching, reliability, and automated testing.
                    </p>

                    <div class="hero-actions">
                        <a href="https://github.com/DujeVidas/url-shortener-api" target="_blank"
                            rel="noopener noreferrer" class="source-link">
                            View Source <span>↗</span>
                        </a>
                    </div>
                </div>

                <div class="architecture-preview">
                    <div class="preview-header">
                        <span>SYSTEM OVERVIEW</span>
                        <span>01 / API</span>
                    </div>

                    <div class="preview-body">
                        <div class="system-node client-node">
                            <span class="node-label">CLIENT</span>
                            <strong>HTTP Request</strong>
                            <small>REST / JSON</small>
                        </div>

                        <div class="flow-arrow">↓</div>

                        <div class="system-node api-node">
                            <span class="node-label">APPLICATION</span>
                            <strong>FastAPI</strong>
                            <small>Python · Pydantic</small>
                        </div>

                        <div class="flow-arrow">↓</div>

                        <div class="database-row">
                            <div class="system-node database-node">
                                <span class="node-label">PERSISTENCE</span>
                                <strong>PostgreSQL</strong>
                                <small>URLs · Analytics</small>
                            </div>

                            <div class="system-node database-node">
                                <span class="node-label">CACHE</span>
                                <strong>Redis</strong>
                                <small>Lookups · Rate Limits</small>
                            </div>
                        </div>
                    </div>

                    <div class="preview-footer">
                        <span>POSTGRESQL + REDIS</span>
                        <span>DOCKERIZED</span>
                    </div>
                </div>
            </div>

            <div class="hero-meta">
                <div class="meta-item">
                    <span class="meta-label">TYPE</span>
                    <span class="meta-value">REST API / Backend</span>
                </div>

                <div class="meta-item">
                    <span class="meta-label">STACK</span>
                    <span class="meta-value">
                        Python · FastAPI · PostgreSQL · Redis
                    </span>
                </div>

                <div class="meta-item">
                    <span class="meta-label">TOOLING</span>
                    <span class="meta-value">
                        Docker · pytest · GitHub Actions
                    </span>
                </div>
            </div>
        </section>
        <section class="overview-section">
            <div class="section-header">
                <span class="section-number">01 / OVERVIEW</span>
                <span class="section-line"></span>
            </div>

            <div class="overview-layout">
                <div class="overview-heading">
                    <h2>
                        More than<br />
                        a shorter link.
                    </h2>
                </div>

                <div class="overview-content">
                    <p class="overview-lead">
                        A URL shortener is simple on the surface:
                        turn a long address into a short one.
                        Building a reliable service around that
                        interaction is a different challenge.
                    </p>

                    <p>
                        This project explores the backend engineering
                        behind that seemingly small operation.
                        It combines a REST API, persistent storage,
                        caching, click analytics, and secure URL
                        management into a single Dockerized system.
                    </p>

                    <p>
                        PostgreSQL acts as the source of truth,
                        while Redis accelerates URL lookups and
                        enforces rate limits. FastAPI handles request
                        validation, routing, authorization, and
                        structured API responses.
                    </p>

                    <p>
                        The application is supported by automated
                        testing and continuous integration, with
                        particular attention to security, predictable
                        behavior, and maintainability.
                    </p>
                </div>
            </div>

            <div class="overview-facts">
                <div class="fact">
                    <span class="fact-value">235</span>
                    <span class="fact-label">PASSING TESTS</span>
                </div>

                <div class="fact">
                    <span class="fact-value">90%</span>
                    <span class="fact-label">MINIMUM COVERAGE GATE</span>
                </div>

                <div class="fact">
                    <span class="fact-value">3</span>
                    <span class="fact-label">DOCKER SERVICES</span>
                </div>

                <div class="fact">
                    <span class="fact-value">REST</span>
                    <span class="fact-label">API ARCHITECTURE</span>
                </div>
            </div>
        </section>
        <section class="architecture-section">
            <div class="section-header">
                <span class="section-number">02 / ARCHITECTURE</span>
                <span class="section-line"></span>
            </div>

            <div class="architecture-intro">
                <h2>
                    Built around<br />
                    clear responsibilities.
                </h2>

                <p>
                    FastAPI handles HTTP requests and application logic.
                    PostgreSQL provides durable storage for URLs and click
                    events. Redis supports fast URL lookups and enforces
                    creation rate limits.
                </p>
            </div>

            <div class="architecture-diagram">
                <div class="diagram-top">
                    <span>SYSTEM ARCHITECTURE</span>
                    <span>FASTAPI / POSTGRESQL / REDIS</span>
                </div>

                <div class="diagram-content">
                    <div class="architecture-node request-node">
                        <span class="architecture-node-label">01 / ENTRY POINT</span>
                        <strong>HTTP Client</strong>
                        <small>Requests · Redirects · JSON</small>
                    </div>

                    <div class="diagram-connector">
                        <span>HTTP</span>
                        <div class="connector-line"></div>
                        <span class="connector-arrow">↓</span>
                    </div>

                    <div class="architecture-node fastapi-node">
                        <span class="architecture-node-label">02 / APPLICATION</span>
                        <strong>FastAPI</strong>
                        <small>Validation · Routing · Authorization</small>
                    </div>

                    <div class="diagram-branches">
                        <div class="diagram-branch">
                            <div class="branch-connector">
                                <span class="connector-arrow">↓</span>
                            </div>

                            <div class="architecture-node storage-node">
                                <span class="architecture-node-label">03 / PERSISTENCE</span>
                                <strong>PostgreSQL</strong>
                                <small>Short URLs · Click Events</small>
                            </div>

                            <p class="branch-description">
                                The source of truth for URL records,
                                management-token hashes, and analytics.
                            </p>
                        </div>

                        <div class="diagram-branch">
                            <div class="branch-connector">
                                <span class="connector-arrow">↓</span>
                            </div>

                            <div class="architecture-node storage-node">
                                <span class="architecture-node-label">04 / PERFORMANCE</span>
                                <strong>Redis</strong>
                                <small>URL Cache · Rate Limiting</small>
                            </div>

                            <p class="branch-description">
                                Reduces repeated database lookups and
                                coordinates atomic request limits.
                            </p>
                        </div>
                    </div>
                </div>

                <div class="diagram-bottom">
                    <span>DOCKER COMPOSE</span>
                    <span>3 SERVICES</span>
                </div>
            </div>

            <div class="architecture-flow">
                <div class="flow-heading">
                    <span>REQUEST FLOW</span>
                    <h3>What happens when someone opens a short link?</h3>
                </div>

                <div class="flow-steps">
                    <div class="flow-step">
                        <span class="flow-step-number">01</span>
                        <h4>Receive</h4>
                        <p>
                            FastAPI receives the short code from the
                            incoming redirect request.
                        </p>
                    </div>

                    <div class="flow-step">
                        <span class="flow-step-number">02</span>
                        <h4>Resolve</h4>
                        <p>
                            Redis is checked for cached URL data.
                            A cache miss requires a PostgreSQL lookup.
                        </p>
                    </div>

                    <div class="flow-step">
                        <span class="flow-step-number">03</span>
                        <h4>Record</h4>
                        <p>
                            The application records a click event
                            for analytics in PostgreSQL.
                        </p>
                    </div>

                    <div class="flow-step">
                        <span class="flow-step-number">04</span>
                        <h4>Redirect</h4>
                        <p>
                            An active short code returns an HTTP 307
                            redirect to the original destination.
                        </p>
                    </div>
                </div>
            </div>
        </section>
        <section class="api-section">
            <div class="section-header">
                <span class="section-number">03 / API DESIGN</span>
                <span class="section-line"></span>
            </div>

            <div class="api-intro">
                <h2>
                    Small interface.<br />
                    Clear behavior.
                </h2>

                <p>
                    The API exposes a focused set of endpoints for creating
                    shortened URLs, resolving redirects, retrieving analytics,
                    and managing links. Each operation uses standard HTTP
                    methods and explicit response behavior.
                </p>
            </div>

            <div class="api-endpoints">
                <div class="endpoint-row">
                    <span class="endpoint-method method-post">POST</span>
                    <code class="endpoint-path">/api/v1/urls</code>
                    <span class="endpoint-description">Create a shortened URL</span>
                    <span class="endpoint-access">PUBLIC · RATE LIMITED</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-get">GET</span>
                    <code class="endpoint-path">/{short_code}</code>
                    <span class="endpoint-description">Redirect to original URL</span>
                    <span class="endpoint-access">PUBLIC</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-get">GET</span>
                    <code class="endpoint-path">
        /api/v1/urls/{short_code}/analytics
      </code>
                    <span class="endpoint-description">Retrieve click analytics</span>
                    <span class="endpoint-access">TOKEN REQUIRED</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-delete">DELETE</span>
                    <code class="endpoint-path">/api/v1/urls/{short_code}</code>
                    <span class="endpoint-description">Deactivate a short URL</span>
                    <span class="endpoint-access">TOKEN REQUIRED</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-get">GET</span>
                    <code class="endpoint-path">/health/live</code>
                    <span class="endpoint-description">Application liveness</span>
                    <span class="endpoint-access">HEALTH</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-get">GET</span>
                    <code class="endpoint-path">/health/ready</code>
                    <span class="endpoint-description">Database and Redis readiness</span>
                    <span class="endpoint-access">HEALTH</span>
                </div>

                <div class="endpoint-row">
                    <span class="endpoint-method method-get">GET</span>
                    <code class="endpoint-path">/api/v1/version</code>
                    <span class="endpoint-description">Application version</span>
                    <span class="endpoint-access">INFO</span>
                </div>
            </div>

            <div class="api-details">
                <div class="api-detail">
                    <span class="api-detail-number">01 / CREATION</span>
                    <h3>Generate a link.</h3>
                    <p>
                        Clients submit a destination URL and can optionally
                        request a custom alias. The API validates the input,
                        generates a unique short code, and returns the new
                        shortened URL alongside its management token.
                    </p>
                </div>

                <div class="api-detail">
                    <span class="api-detail-number">02 / REDIRECTION</span>
                    <h3>Resolve and redirect.</h3>
                    <p>
                        Public requests resolve an active short code and
                        receive an HTTP 307 redirect. Redis caching reduces
                        repeated database lookups while PostgreSQL remains
                        the source of truth.
                    </p>
                </div>

                <div class="api-detail">
                    <span class="api-detail-number">03 / MANAGEMENT</span>
                    <h3>Control access.</h3>
                    <p>
                        Analytics and deactivation require the correct
                        management token in the X-Management-Token header.
                        Unauthorized requests cannot access protected
                        analytics or deactivate a link.
                    </p>
                </div>
            </div>

            <div class="api-docs-note">
                <div>
                    <span class="api-docs-label">API DOCUMENTATION</span>
                    <p>
                        Interactive OpenAPI documentation is available
                        through FastAPI's built-in Swagger UI at
                        <code>/docs</code> when the service is running.
                    </p>
                </div>

                <a href="https://github.com/DujeVidas/url-shortener-api" target="_blank" rel="noopener noreferrer"
                    class="api-docs-link">
                    View Source <span>↗</span>
                </a>
            </div>
        </section>
        <section class="security-section">
            <div class="section-header">
                <span class="section-number">04 / SECURITY</span>
                <span class="section-line"></span>
            </div>

            <div class="security-intro">
                <h2>
                    Public redirects.<br />
                    Private control.
                </h2>

                <p>
                    Anyone can follow a shortened URL, but only someone
                    holding its management token can access analytics or
                    deactivate it. This separates public functionality
                    from privileged operations without requiring a
                    traditional user-account system.
                </p>
            </div>

            <div class="security-diagram">
                <div class="security-diagram-header">
                    <span>MANAGEMENT TOKEN LIFECYCLE</span>
                    <span>CAPABILITY-BASED AUTHORIZATION</span>
                </div>

                <div class="token-flow">
                    <div class="token-step">
                        <span class="token-step-number">01 / GENERATE</span>
                        <h3>Random token</h3>
                        <code>secrets.token_urlsafe(32)</code>
                        <p>
                            A cryptographically secure token is generated
                            when a new short URL is created.
                        </p>
                    </div>

                    <div class="token-step">
                        <span class="token-step-number">02 / STORE</span>
                        <h3>Hash only</h3>
                        <code>SHA-256(token)</code>
                        <p>
                            PostgreSQL stores the token hash, not the
                            original secret.
                        </p>
                    </div>

                    <div class="token-step">
                        <span class="token-step-number">03 / RETURN</span>
                        <h3>One-time delivery</h3>
                        <code>201 Created</code>
                        <p>
                            The original token is returned to the client
                            during URL creation and cannot be recovered later.
                        </p>
                    </div>

                    <div class="token-step">
                        <span class="token-step-number">04 / VERIFY</span>
                        <h3>Authorize request</h3>
                        <code>X-Management-Token</code>
                        <p>
                            Protected operations verify the supplied token
                            before granting access.
                        </p>
                    </div>
                </div>

                <div class="security-diagram-footer">
                    <span>256 BITS OF TOKEN RANDOMNESS</span>
                    <span>SHA-256 STORAGE</span>
                </div>
            </div>

            <div class="security-details">
                <div class="security-detail">
                    <span class="security-detail-index">01</span>
                    <div>
                        <h3>Cryptographically secure generation</h3>
                        <p>
                            Python's secrets module generates unpredictable
                            management tokens. Each token is unique to its
                            shortened URL and acts as a capability granting
                            access to protected operations.
                        </p>
                    </div>
                </div>

                <div class="security-detail">
                    <span class="security-detail-index">02</span>
                    <div>
                        <h3>Hash-based verification</h3>
                        <p>
                            Only SHA-256 token hashes are persisted in
                            PostgreSQL. Verification uses
                            <code>secrets.compare_digest</code> to compare
                            values without a conventional early-exit
                            string comparison.
                        </p>
                    </div>
                </div>

                <div class="security-detail">
                    <span class="security-detail-index">03</span>
                    <div>
                        <h3>Protected management endpoints</h3>
                        <p>
                            Analytics retrieval and URL deactivation require
                            the correct token in the
                            <code>X-Management-Token</code> header.
                            Missing or invalid tokens result in HTTP 403.
                        </p>
                    </div>
                </div>

                <div class="security-detail">
                    <span class="security-detail-index">04</span>
                    <div>
                        <h3>Safe deactivation</h3>
                        <p>
                            Deactivation is authorized before the URL record
                            is changed and its Redis cache entry is
                            invalidated. Unauthorized requests cannot
                            deactivate another link.
                        </p>
                    </div>
                </div>
            </div>

            <div class="security-note">
                <span>DESIGN DECISION</span>
                <p>
                    Management tokens provide per-link authorization
                    without introducing accounts, sessions, or a full
                    authentication service. The tradeoff is intentional:
                    whoever possesses the token controls the link, so
                    clients must store it securely.
                </p>
            </div>
        </section>
        <section class="performance-section">
            <div class="section-header">
                <span class="section-number">05 / PERFORMANCE & RELIABILITY</span>
                <span class="section-line"></span>
            </div>

            <div class="performance-intro">
                <h2>
                    Fast lookups.<br />
                    Controlled access.
                </h2>

                <p>
                    Redis serves two distinct roles in the application:
                    caching frequently accessed URL data and coordinating
                    rate limits. PostgreSQL remains the persistent source
                    of truth for shortened URLs and click analytics.
                </p>
            </div>

            <div class="performance-diagram">
                <div class="performance-diagram-header">
                    <span>REDIRECT LOOKUP STRATEGY</span>
                    <span>CACHE-ASIDE PATTERN</span>
                </div>

                <div class="cache-flow">
                    <div class="cache-entry">
                        <span class="cache-label">01 / REQUEST</span>
                        <strong>Short code received</strong>
                        <code>GET /{short_code}</code>
                    </div>

                    <div class="cache-arrow">↓</div>

                    <div class="cache-entry cache-primary">
                        <span class="cache-label">02 / LOOKUP</span>
                        <strong>Redis cache</strong>
                        <small>Check for cached URL data</small>
                    </div>

                    <div class="cache-paths">
                        <div class="cache-path">
                            <span class="path-status">CACHE HIT</span>
                            <div class="path-arrow">↓</div>
                            <div class="cache-result">
                                <strong>Use cached data</strong>
                                <small>No database lookup required</small>
                            </div>
                        </div>

                        <div class="cache-path">
                            <span class="path-status">CACHE MISS</span>
                            <div class="path-arrow">↓</div>
                            <div class="cache-result">
                                <strong>Query PostgreSQL</strong>
                                <small>Resolve URL and populate cache</small>
                            </div>
                        </div>
                    </div>

                    <div class="cache-end-note">
                        Valid, active URLs return an HTTP 307 redirect.
                        Click analytics are recorded separately in PostgreSQL.
                    </div>
                </div>

                <div class="performance-diagram-footer">
                    <span>REDIS / CACHE</span>
                    <span>POSTGRESQL / SOURCE OF TRUTH</span>
                </div>
            </div>

            <div class="performance-features">
                <div class="performance-feature">
                    <span class="performance-feature-number">01 / CACHING</span>

                    <h3>Reduce repeated lookups.</h3>

                    <p>
                        Redis stores URL lookup data so repeated redirects
                        can avoid unnecessary PostgreSQL queries. On a
                        cache miss, the application resolves the short code
                        using persistent storage and caches the result.
                    </p>
                </div>

                <div class="performance-feature">
                    <span class="performance-feature-number">02 / INVALIDATION</span>

                    <h3>Keep cached state consistent.</h3>

                    <p>
                        Deactivating a link also invalidates its Redis
                        cache entry. This prevents a previously cached
                        destination from remaining available after
                        authorized deactivation.
                    </p>
                </div>

                <div class="performance-feature">
                    <span class="performance-feature-number">03 / RATE LIMITING</span>

                    <h3>Enforce limits atomically.</h3>

                    <p>
                        URL creation is protected by Redis-backed rate
                        limiting. A Lua script performs the rate-limit
                        operation atomically, avoiding race conditions
                        between concurrent requests.
                    </p>
                </div>
            </div>

            <div class="rate-limit-panel">
                <div class="rate-limit-main">
                    <span class="rate-limit-eyebrow">DEFAULT DOCKER CONFIGURATION</span>

                    <div class="rate-limit-value">
                        <strong>10</strong>
                        <span>
                            URL creations<br />
                            per 60 seconds
                        </span>
                    </div>
                </div>

                <div class="rate-limit-details">
                    <div class="rate-limit-detail">
                        <span>429 / TOO MANY REQUESTS</span>
                        <p>
                            Requests exceeding the configured limit receive
                            HTTP 429 and a Retry-After response header.
                        </p>
                    </div>

                    <div class="rate-limit-detail">
                        <span>503 / SERVICE UNAVAILABLE</span>
                        <p>
                            If the Redis-backed rate limiter fails, URL
                            creation returns HTTP 503 rather than silently
                            bypassing the protection.
                        </p>
                    </div>
                </div>
            </div>

            <div class="performance-note">
                <span>ENGINEERING TRADEOFF</span>

                <p>
                    Caching introduces another layer of state that must
                    be kept consistent. The goal is not simply to make
                    requests faster, but to balance performance with
                    predictable behavior and safe URL management.
                </p>
            </div>
        </section>
        <section class="testing-section">
            <div class="section-header">
                <span class="section-number">06 / TESTING & CI</span>
                <span class="section-line"></span>
            </div>

            <div class="testing-intro">
                <h2>
                    Built to work.<br />
                    Tested to stay that way.
                </h2>

                <p>
                    Automated testing covers the API's core behavior,
                    security boundaries, caching, rate limiting, and
                    documented contracts. GitHub Actions runs quality
                    checks and integration tests to catch regressions
                    before changes are merged.
                </p>
            </div>

            <div class="testing-stats">
                <div class="testing-stat">
                    <span class="testing-stat-label">AUTOMATED TESTS</span>
                    <strong>235</strong>
                    <span class="testing-stat-caption">Passing tests</span>
                </div>

                <div class="testing-stat">
                    <span class="testing-stat-label">COVERAGE GATE</span>
                    <strong>90<span class="stat-unit">%</span></strong>
                    <span class="testing-stat-caption">
                        Minimum combined statement and branch coverage
                    </span>
                </div>

                <div class="testing-stat">
                    <span class="testing-stat-label">CI STATUS</span>
                    <strong class="ci-status">
                        <span class="ci-status-dot"></span>
                        Passed
                    </strong>
                    <span class="testing-stat-caption">
                        Both GitHub Actions jobs passed
                    </span>
                </div>
            </div>

            <div class="testing-content">
                <div class="testing-column">
                    <span class="testing-column-label">01 / TEST COVERAGE</span>
                    <h3>Beyond the happy path.</h3>

                    <p>
                        Tests verify expected API behavior as well as
                        failure cases and protected operations.
                    </p>

                    <div class="test-categories">
                        <div class="test-category">
                            <span>01</span>
                            <div>
                                <h4>URL lifecycle</h4>
                                <p>Creation, redirection, analytics, and deactivation.</p>
                            </div>
                        </div>

                        <div class="test-category">
                            <span>02</span>
                            <div>
                                <h4>Security</h4>
                                <p>Token generation, verification, and authorization.</p>
                            </div>
                        </div>

                        <div class="test-category">
                            <span>03</span>
                            <div>
                                <h4>Infrastructure behavior</h4>
                                <p>Redis caching, invalidation, and rate limiting.</p>
                            </div>
                        </div>

                        <div class="test-category">
                            <span>04</span>
                            <div>
                                <h4>API contracts</h4>
                                <p>Validation, HTTP responses, and OpenAPI schemas.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="testing-column">
                    <span class="testing-column-label">02 / CONTINUOUS INTEGRATION</span>
                    <h3>Checks on every change.</h3>

                    <p>
                        GitHub Actions automates code-quality checks,
                        application tests, container validation, and
                        end-to-end API verification.
                    </p>

                    <div class="ci-pipeline">
                        <div class="ci-step">
                            <span class="ci-step-number">01</span>
                            <div>
                                <strong>Code quality</strong>
                                <small>Ruff linting and formatting checks</small>
                            </div>
                            <span class="ci-step-check">✓</span>
                        </div>

                        <div class="ci-step">
                            <span class="ci-step-number">02</span>
                            <div>
                                <strong>Automated tests</strong>
                                <small>pytest and coverage enforcement</small>
                            </div>
                            <span class="ci-step-check">✓</span>
                        </div>

                        <div class="ci-step">
                            <span class="ci-step-number">03</span>
                            <div>
                                <strong>Container validation</strong>
                                <small>Docker build and Compose checks</small>
                            </div>
                            <span class="ci-step-check">✓</span>
                        </div>

                        <div class="ci-step">
                            <span class="ci-step-number">04</span>
                            <div>
                                <strong>Integration checks</strong>
                                <small>Liveness, readiness, and URL lifecycle</small>
                            </div>
                            <span class="ci-step-check">✓</span>
                        </div>

                        <div class="ci-step">
                            <span class="ci-step-number">05</span>
                            <div>
                                <strong>Security & rate limiting</strong>
                                <small>Protected operations and request limits</small>
                            </div>
                            <span class="ci-step-check">✓</span>
                        </div>
                    </div>
                </div>
            </div>

            <div class="testing-note">
                <span>QUALITY ENGINEERING</span>

                <p>
                    The objective is not simply to accumulate tests,
                    but to make important behavior repeatable and
                    verifiable—from authorization rules to infrastructure
                    failures and complete API workflows.
                </p>
            </div>
        </section>
        <section class="conclusion-section">
            <div class="section-header">
                <span class="section-number">07 / CONCLUSION</span>
                <span class="section-line"></span>
            </div>

            <div class="conclusion-layout">
                <div class="conclusion-heading">
                    <h2>
                        Simple idea.<br />
                        Real engineering.
                    </h2>
                </div>

                <div class="conclusion-content">
                    <p class="conclusion-lead">
                        Shortening a URL is straightforward.
                        Building the system around it required
                        thinking about persistence, security,
                        concurrency, caching, and reliability.
                    </p>

                    <p>
                        This project brought those concerns together
                        in a backend service built with FastAPI,
                        PostgreSQL, and Redis. It goes beyond the
                        basic create-and-redirect workflow by adding
                        protected analytics, per-link authorization,
                        cache invalidation, and distributed rate limiting.
                    </p>

                    <p>
                        Automated tests, database migrations, Docker,
                        and GitHub Actions helped make the application
                        reproducible and easier to maintain.
                    </p>
                </div>
            </div>

            <div class="conclusion-takeaways">
                <div class="takeaway">
                    <span class="takeaway-number">01 / SECURITY</span>
                    <h3>Design access deliberately.</h3>
                    <p>
                        Public redirects and protected management
                        operations have different security requirements.
                        Per-URL management tokens provide a focused
                        authorization mechanism without requiring
                        user accounts.
                    </p>
                </div>

                <div class="takeaway">
                    <span class="takeaway-number">02 / ARCHITECTURE</span>
                    <h3>Give each system a purpose.</h3>
                    <p>
                        PostgreSQL handles durable data storage,
                        while Redis provides caching and atomic
                        rate limiting. The architecture separates
                        persistence from performance concerns.
                    </p>
                </div>

                <div class="takeaway">
                    <span class="takeaway-number">03 / RELIABILITY</span>
                    <h3>Make behavior verifiable.</h3>
                    <p>
                        Automated testing and CI checks help
                        catch regressions across API behavior,
                        authorization, infrastructure integration,
                        and complete URL workflows.
                    </p>
                </div>
            </div>

            <div class="conclusion-footer">
                <div class="conclusion-footer-copy">
                    <span>EXPLORE THE PROJECT</span>
                    <h3>See how it was built.</h3>
                    <p>
                        Explore the source code, API implementation,
                        tests, Docker configuration, and CI workflows
                        on GitHub.
                    </p>
                </div>

                <div class="conclusion-actions">
                    <a href="https://github.com/DujeVidas/url-shortener-api" target="_blank" rel="noopener noreferrer"
                        class="conclusion-source-link">
                        View Source <span>↗</span>
                    </a>

                    <NuxtLink to="/" class="conclusion-back-link">
                        Back to all work <span>↗</span>
                    </NuxtLink>
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped>
.project-page {
    width: 100%;
}

.project-hero {
    padding: 32px 0 96px;
}

.hero-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 24px;
    margin-bottom: 96px;
}

.back-link {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    color: inherit;
    text-decoration: none;
    font-size: 13px;
}

.back-link:hover {
    opacity: 0.55;
}

.project-index,
.eyebrow,
.node-label,
.preview-header,
.preview-footer,
.meta-label {
    font-size: 11px;
    letter-spacing: 0.12em;
    text-transform: uppercase;
}

.project-index {
    opacity: 0.45;
}

.hero-content {
    display: grid;
    grid-template-columns: minmax(0, 1.2fr) minmax(0, 0.8fr);
    gap: 64px;
    align-items: center;
}

.eyebrow {
    margin: 0 0 28px;
    opacity: 0.55;
}

.hero-copy h1 {
    margin: 0;
    font-size: clamp(48px, 6.5vw, 104px);
    line-height: 0.98;
    letter-spacing: -0.065em;
    font-weight: 500;
}

.hero-copy h1 span {
    display: block;
}

.hero-description {
    max-width: 550px;
    margin: 36px 0 0;
    font-size: clamp(15px, 1.3vw, 18px);
    line-height: 1.8;
    opacity: 0.65;
}

.hero-actions {
    display: flex;
    gap: 24px;
    margin-top: 36px;
}

.source-link {
    display: inline-flex;
    align-items: center;
    justify-content: space-between;
    gap: 40px;
    padding: 14px 18px;
    border: 1px solid currentColor;
    color: inherit;
    text-decoration: none;
    font-size: 12px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    transition: background 0.2s, color 0.2s;
}

.source-link:hover {
    background: #111;
    color: #fff;
}

.architecture-preview {
    border: 1px solid currentColor;
    min-width: 0;
}

.preview-header,
.preview-footer {
    display: flex;
    justify-content: space-between;
    gap: 12px;
    padding: 16px 20px;
    opacity: 0.65;
}

.preview-header {
    border-bottom: 1px solid currentColor;
}

.preview-footer {
    border-top: 1px solid currentColor;
}

.preview-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 42px 24px;
}

.system-node {
    display: flex;
    flex-direction: column;
    gap: 8px;
    padding: 18px;
    border: 1px solid currentColor;
    width: 100%;
    text-align: center;
}

.system-node strong {
    font-size: 18px;
    font-weight: 500;
}

.system-node small {
    font-size: 11px;
    opacity: 0.5;
}

.node-label {
    opacity: 0.5;
}

.client-node {
    max-width: 230px;
}

.api-node {
    max-width: 230px;
    background: #111;
    color: #fff;
}

.flow-arrow {
    padding: 14px 0;
    font-size: 22px;
    line-height: 1;
}

.database-row {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 12px;
    width: 100%;
}

.database-node {
    min-width: 0;
}

.hero-meta {
    display: grid;
    grid-template-columns: 1fr 2fr 1.5fr;
    gap: 32px;
    padding-top: 28px;
    margin-top: 96px;
    border-top: 1px solid currentColor;
}

.meta-item {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.meta-label {
    opacity: 0.45;
}

.meta-value {
    font-size: 13px;
    line-height: 1.6;
}

@media (max-width: 900px) {
    .hero-top {
        margin-bottom: 64px;
    }

    .hero-content {
        grid-template-columns: 1fr;
        gap: 56px;
    }

    .architecture-preview {
        max-width: 600px;
    }

    .hero-meta {
        grid-template-columns: repeat(2, minmax(0, 1fr));
        margin-top: 64px;
    }
}

@media (max-width: 600px) {
    .project-hero {
        padding: 24px 0 64px;
    }

    .hero-top {
        align-items: flex-start;
        margin-bottom: 56px;
    }

    .project-index {
        text-align: right;
    }

    .hero-copy h1 {
        font-size: clamp(44px, 12vw, 72px);
    }

    .hero-description {
        margin-top: 28px;
    }

    .preview-body {
        padding: 28px 14px;
    }

    .system-node {
        padding: 14px 8px;
    }

    .system-node strong {
        font-size: 15px;
    }

    .hero-meta {
        grid-template-columns: 1fr;
        gap: 24px;
        margin-top: 56px;
    }
}


.overview-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.section-header {
    display: flex;
    align-items: center;
    gap: 24px;
    margin-bottom: 72px;
}

.section-number {
    font-size: 11px;
    letter-spacing: 0.12em;
    white-space: nowrap;
}

.section-line {
    flex: 1;
    height: 1px;
    background: currentColor;
    opacity: 0.2;
}

.overview-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
}

.overview-heading h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.overview-content {
    max-width: 560px;
}

.overview-content p {
    margin: 0 0 24px;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}

.overview-content .overview-lead {
    font-size: clamp(19px, 2vw, 25px);
    line-height: 1.5;
    opacity: 1;
    margin-bottom: 32px;
}

.overview-facts {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    margin-top: 88px;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.fact {
    display: flex;
    flex-direction: column;
    gap: 14px;
    padding: 32px 24px;
}

.fact:first-child {
    padding-left: 0;
}

.fact+.fact {
    border-left: 1px solid currentColor;
}

.fact-value {
    font-size: clamp(28px, 3.5vw, 48px);
    line-height: 1;
    letter-spacing: -0.05em;
    font-weight: 500;
}

.fact-label {
    font-size: 10px;
    line-height: 1.5;
    letter-spacing: 0.1em;
    opacity: 0.5;
}

@media (max-width: 900px) {
    .overview-section {
        padding: 80px 0;
    }

    .overview-layout {
        grid-template-columns: 1fr;
        gap: 40px;
    }

    .overview-facts {
        grid-template-columns: repeat(2, minmax(0, 1fr));
        margin-top: 64px;
    }

    .fact {
        padding: 28px 20px;
    }

    .fact:first-child {
        padding-left: 20px;
    }

    .fact:nth-child(3) {
        border-left: 0;
    }

    .fact:nth-child(n + 3) {
        border-top: 1px solid currentColor;
    }
}

@media (max-width: 600px) {
    .overview-section {
        padding: 64px 0;
    }

    .section-header {
        margin-bottom: 48px;
    }

    .overview-heading h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .overview-content p {
        font-size: 14px;
    }

    .overview-content .overview-lead {
        font-size: 19px;
    }

    .fact {
        padding: 24px 14px;
    }

    .fact:first-child {
        padding-left: 14px;
    }

    .fact-value {
        font-size: 32px;
    }
}


.architecture-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.architecture-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: end;
    margin-bottom: 72px;
}

.architecture-intro h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.architecture-intro p {
    max-width: 540px;
    margin: 0;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}

.architecture-diagram {
    border: 1px solid currentColor;
}

.diagram-top,
.diagram-bottom {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    padding: 18px 24px;
    font-size: 10px;
    letter-spacing: 0.12em;
}

.diagram-top {
    border-bottom: 1px solid currentColor;
}

.diagram-bottom {
    border-top: 1px solid currentColor;
}

.diagram-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 56px 32px;
}

.architecture-node {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    width: 100%;
    padding: 24px 20px;
    border: 1px solid currentColor;
    text-align: center;
}

.architecture-node-label {
    font-size: 10px;
    letter-spacing: 0.1em;
    opacity: 0.55;
}

.architecture-node strong {
    font-size: clamp(20px, 2.5vw, 30px);
    font-weight: 500;
    letter-spacing: -0.04em;
}

.architecture-node small {
    font-size: 12px;
    opacity: 0.6;
}

.request-node,
.fastapi-node {
    max-width: 420px;
}

.fastapi-node {
    background: #111;
    color: #fff;
}

.diagram-connector {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    font-size: 10px;
    letter-spacing: 0.1em;
    padding-top: 16px;
}

.connector-line {
    height: 24px;
    width: 1px;
    background: currentColor;
}

.connector-arrow {
    font-size: 22px;
    line-height: 1;
}

.diagram-branches {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 24px;
    width: 100%;
    max-width: 850px;
}

.diagram-branch {
    min-width: 0;
}

.branch-connector {
    display: flex;
    justify-content: center;
    padding: 18px 0;
}

.storage-node {
    min-height: 150px;
    justify-content: center;
}

.branch-description {
    max-width: 300px;
    margin: 18px auto 0;
    font-size: 12px;
    line-height: 1.8;
    text-align: center;
    opacity: 0.6;
}

.architecture-flow {
    margin-top: 96px;
}

.flow-heading {
    display: flex;
    justify-content: space-between;
    align-items: start;
    gap: 32px;
    margin-bottom: 36px;
}

.flow-heading>span {
    font-size: 11px;
    letter-spacing: 0.12em;
    white-space: nowrap;
}

.flow-heading h3 {
    max-width: 620px;
    margin: 0;
    font-size: clamp(24px, 3vw, 40px);
    line-height: 1.2;
    letter-spacing: -0.04em;
    font-weight: 500;
}

.flow-steps {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.flow-step {
    padding: 28px 24px 32px;
}

.flow-step:first-child {
    padding-left: 0;
}

.flow-step+.flow-step {
    border-left: 1px solid currentColor;
}

.flow-step-number {
    font-size: 11px;
    opacity: 0.5;
}

.flow-step h4 {
    margin: 28px 0 14px;
    font-size: 22px;
    font-weight: 500;
    letter-spacing: -0.04em;
}

.flow-step p {
    margin: 0;
    font-size: 13px;
    line-height: 1.8;
    opacity: 0.65;
}

@media (max-width: 900px) {
    .architecture-section {
        padding: 80px 0;
    }

    .architecture-intro {
        grid-template-columns: 1fr;
        gap: 32px;
    }

    .flow-steps {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .flow-step {
        padding: 28px 20px;
    }

    .flow-step:first-child {
        padding-left: 20px;
    }

    .flow-step:nth-child(3) {
        border-left: 0;
    }

    .flow-step:nth-child(n + 3) {
        border-top: 1px solid currentColor;
    }
}

@media (max-width: 600px) {
    .architecture-section {
        padding: 64px 0;
    }

    .architecture-intro {
        margin-bottom: 48px;
    }

    .architecture-intro h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .architecture-intro p {
        font-size: 14px;
    }

    .diagram-top,
    .diagram-bottom {
        padding: 14px;
        font-size: 9px;
    }

    .diagram-content {
        padding: 36px 14px;
    }

    .architecture-node {
        padding: 20px 10px;
    }

    .architecture-node strong {
        font-size: 20px;
    }

    .architecture-node small {
        font-size: 10px;
    }

    .diagram-branches {
        gap: 10px;
    }

    .storage-node {
        min-height: 160px;
    }

    .branch-description {
        font-size: 11px;
    }

    .architecture-flow {
        margin-top: 72px;
    }

    .flow-heading {
        flex-direction: column;
        gap: 20px;
    }

    .flow-steps {
        grid-template-columns: 1fr;
    }

    .flow-step,
    .flow-step:first-child {
        padding: 24px 0;
        border-left: 0;
    }

    .flow-step+.flow-step {
        border-top: 1px solid currentColor;
    }

    .flow-step h4 {
        margin-top: 18px;
    }
}


.api-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.api-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: end;
    margin-bottom: 72px;
}

.api-intro h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.api-intro>p {
    max-width: 540px;
    margin: 0;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}

.api-endpoints {
    border-top: 1px solid currentColor;
}

.endpoint-row {
    display: grid;
    grid-template-columns: 90px minmax(0, 2fr) minmax(0, 1.4fr) 150px;
    gap: 20px;
    align-items: center;
    padding: 25px 18px;
    border-bottom: 1px solid currentColor;
}

.endpoint-method {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    width: 70px;
    padding: 8px 0;
    border: 1px solid currentColor;
    font-size: 10px;
    font-weight: 600;
    letter-spacing: 0.08em;
}

.method-post {
    background: #111;
    color: #fff;
}

.method-get {
    background: transparent;
}

.method-delete {
    border-style: dashed;
}

.endpoint-path {
    min-width: 0;
    overflow-wrap: anywhere;
    font-family: monospace;
    font-size: 13px;
}

.endpoint-description {
    font-size: 13px;
    line-height: 1.6;
    opacity: 0.7;
}

.endpoint-access {
    font-size: 10px;
    letter-spacing: 0.08em;
    text-align: right;
    opacity: 0.5;
}

.api-details {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 40px;
    margin-top: 88px;
}

.api-detail {
    border-top: 1px solid currentColor;
    padding-top: 24px;
}

.api-detail-number {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.api-detail h3 {
    margin: 30px 0 18px;
    font-size: clamp(22px, 2.5vw, 32px);
    line-height: 1.2;
    letter-spacing: -0.04em;
    font-weight: 500;
}

.api-detail p {
    max-width: 380px;
    margin: 0;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}

.api-docs-note {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 40px;
    margin-top: 88px;
    padding: 30px 0;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.api-docs-label {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.api-docs-note p {
    max-width: 560px;
    margin: 14px 0 0;
    font-size: 13px;
    line-height: 1.8;
    opacity: 0.7;
}

.api-docs-note code {
    font-family: monospace;
    font-size: 12px;
}

.api-docs-link {
    display: inline-flex;
    align-items: center;
    justify-content: space-between;
    gap: 32px;
    flex-shrink: 0;
    padding: 14px 18px;
    border: 1px solid currentColor;
    color: inherit;
    text-decoration: none;
    font-size: 11px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: background 0.2s, color 0.2s;
}

.api-docs-link:hover {
    background: #111;
    color: #fff;
}

@media (max-width: 900px) {
    .api-section {
        padding: 80px 0;
    }

    .api-intro {
        grid-template-columns: 1fr;
        gap: 32px;
    }

    .endpoint-row {
        grid-template-columns: 80px minmax(0, 1fr) 120px;
        gap: 16px;
    }

    .endpoint-description {
        grid-column: 2 / 3;
        grid-row: 2;
    }

    .endpoint-access {
        grid-column: 3;
        grid-row: 1 / 3;
    }

    .api-details {
        gap: 24px;
    }
}

@media (max-width: 600px) {
    .api-section {
        padding: 64px 0;
    }

    .api-intro {
        margin-bottom: 48px;
    }

    .api-intro h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .api-intro>p {
        font-size: 14px;
    }

    .endpoint-row {
        grid-template-columns: 70px minmax(0, 1fr);
        gap: 12px;
        padding: 22px 0;
    }

    .endpoint-method {
        width: 60px;
    }

    .endpoint-path {
        font-size: 12px;
    }

    .endpoint-description {
        grid-column: 2;
        grid-row: 2;
    }

    .endpoint-access {
        grid-column: 2;
        grid-row: 3;
        text-align: left;
    }

    .api-details {
        grid-template-columns: 1fr;
        gap: 36px;
        margin-top: 64px;
    }

    .api-detail h3 {
        margin-top: 20px;
    }

    .api-docs-note {
        flex-direction: column;
        align-items: flex-start;
        margin-top: 64px;
    }
}


.security-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.security-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: end;
    margin-bottom: 72px;
}

.security-intro h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.security-intro>p {
    max-width: 540px;
    margin: 0;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}

.security-diagram {
    border: 1px solid currentColor;
}

.security-diagram-header,
.security-diagram-footer {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    padding: 18px 24px;
    font-size: 10px;
    letter-spacing: 0.12em;
}

.security-diagram-header {
    border-bottom: 1px solid currentColor;
}

.security-diagram-footer {
    border-top: 1px solid currentColor;
}

.token-flow {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
}

.token-step {
    min-width: 0;
    padding: 32px 24px 40px;
}

.token-step+.token-step {
    border-left: 1px solid currentColor;
}

.token-step-number {
    display: block;
    font-size: 10px;
    letter-spacing: 0.1em;
    opacity: 0.5;
}

.token-step h3 {
    margin: 40px 0 18px;
    font-size: clamp(20px, 2vw, 28px);
    line-height: 1.2;
    letter-spacing: -0.04em;
    font-weight: 500;
}

.token-step code {
    display: block;
    width: fit-content;
    max-width: 100%;
    padding: 9px 11px;
    border: 1px solid currentColor;
    font-family: monospace;
    font-size: 11px;
    overflow-wrap: anywhere;
}

.token-step p {
    margin: 24px 0 0;
    font-size: 12px;
    line-height: 1.8;
    opacity: 0.65;
}

.security-details {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0 64px;
    margin-top: 88px;
}

.security-detail {
    display: grid;
    grid-template-columns: 42px minmax(0, 1fr);
    gap: 18px;
    padding: 32px 0;
    border-top: 1px solid currentColor;
}

.security-detail-index {
    font-size: 11px;
    opacity: 0.5;
}

.security-detail h3 {
    margin: 0 0 16px;
    font-size: clamp(20px, 2.2vw, 28px);
    font-weight: 500;
    letter-spacing: -0.04em;
}

.security-detail p {
    max-width: 460px;
    margin: 0;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}

.security-detail code {
    font-family: monospace;
    font-size: 12px;
    overflow-wrap: anywhere;
}

.security-note {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 48px;
    margin-top: 64px;
    padding: 32px 0;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.security-note>span {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.security-note p {
    max-width: 720px;
    margin: 0;
    font-size: clamp(17px, 1.8vw, 23px);
    line-height: 1.6;
    letter-spacing: -0.02em;
}

@media (max-width: 900px) {
    .security-section {
        padding: 80px 0;
    }

    .security-intro {
        grid-template-columns: 1fr;
        gap: 32px;
    }

    .token-flow {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .token-step:nth-child(3) {
        border-left: 0;
    }

    .token-step:nth-child(n + 3) {
        border-top: 1px solid currentColor;
    }

    .security-details {
        gap: 0 32px;
    }
}

@media (max-width: 600px) {
    .security-section {
        padding: 64px 0;
    }

    .security-intro {
        margin-bottom: 48px;
    }

    .security-intro h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .security-intro>p {
        font-size: 14px;
    }

    .security-diagram-header,
    .security-diagram-footer {
        padding: 14px;
        font-size: 9px;
    }

    .token-flow {
        grid-template-columns: 1fr;
    }

    .token-step {
        padding: 28px 20px;
    }

    .token-step+.token-step,
    .token-step:nth-child(3) {
        border-left: 0;
        border-top: 1px solid currentColor;
    }

    .token-step h3 {
        margin-top: 24px;
    }

    .security-details {
        grid-template-columns: 1fr;
        margin-top: 64px;
    }

    .security-detail {
        grid-template-columns: 30px minmax(0, 1fr);
        gap: 12px;
    }

    .security-note {
        grid-template-columns: 1fr;
        gap: 20px;
        margin-top: 48px;
    }
}


.performance-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.performance-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: end;
    margin-bottom: 72px;
}

.performance-intro h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.performance-intro>p {
    max-width: 540px;
    margin: 0;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}


.performance-diagram {
    border: 1px solid currentColor;
}

.performance-diagram-header,
.performance-diagram-footer {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    padding: 18px 24px;
    font-size: 10px;
    letter-spacing: 0.12em;
}

.performance-diagram-header {
    border-bottom: 1px solid currentColor;
}

.performance-diagram-footer {
    border-top: 1px solid currentColor;
}

.cache-flow {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 48px 24px;
}

.cache-entry {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    width: 100%;
    max-width: 360px;
    padding: 22px 18px;
    border: 1px solid currentColor;
    text-align: center;
}

.cache-label {
    font-size: 10px;
    letter-spacing: 0.1em;
    opacity: 0.55;
}

.cache-entry strong {
    font-size: 22px;
    font-weight: 500;
    letter-spacing: -0.04em;
}

.cache-entry code,
.cache-entry small {
    font-family: monospace;
    font-size: 12px;
}

.cache-entry small {
    opacity: 0.65;
}

.cache-primary {
    background: #111;
    color: #fff;
}

.cache-arrow,
.path-arrow {
    padding: 14px 0;
    font-size: 22px;
    line-height: 1;
}

.cache-paths {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 24px;
    width: 100%;
    max-width: 760px;
    margin-top: 28px;
}

.cache-path {
    display: flex;
    flex-direction: column;
    align-items: center;
    min-width: 0;
}

.path-status {
    width: 100%;
    padding: 12px;
    border: 1px solid currentColor;
    font-size: 10px;
    letter-spacing: 0.12em;
    text-align: center;
}

.cache-result {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 10px;
    width: 100%;
    min-height: 115px;
    padding: 20px;
    border: 1px solid currentColor;
    text-align: center;
}

.cache-result strong {
    font-size: 18px;
    font-weight: 500;
}

.cache-result small {
    font-size: 11px;
    line-height: 1.6;
    opacity: 0.6;
}

.cache-end-note {
    max-width: 540px;
    margin-top: 40px;
    padding-top: 24px;
    border-top: 1px solid currentColor;
    font-size: 12px;
    line-height: 1.8;
    text-align: center;
    opacity: 0.65;
}


.performance-features {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 40px;
    margin-top: 88px;
}

.performance-feature {
    padding-top: 24px;
    border-top: 1px solid currentColor;
}

.performance-feature-number {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.performance-feature h3 {
    margin: 32px 0 18px;
    font-size: clamp(22px, 2.5vw, 32px);
    line-height: 1.2;
    letter-spacing: -0.04em;
    font-weight: 500;
}

.performance-feature p {
    max-width: 390px;
    margin: 0;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}


.rate-limit-panel {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin-top: 88px;
    border: 1px solid currentColor;
}

.rate-limit-main {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    gap: 48px;
    padding: 40px;
    background: #111;
    color: #fff;
}

.rate-limit-eyebrow {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.6;
}

.rate-limit-value {
    display: flex;
    align-items: end;
    gap: 24px;
}

.rate-limit-value strong {
    font-size: clamp(96px, 12vw, 160px);
    line-height: 0.8;
    letter-spacing: -0.08em;
    font-weight: 500;
}

.rate-limit-value span {
    padding-bottom: 8px;
    font-size: 14px;
    line-height: 1.5;
}

.rate-limit-details {
    display: grid;
    grid-template-rows: 1fr 1fr;
}

.rate-limit-detail {
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 18px;
    padding: 36px;
}

.rate-limit-detail+.rate-limit-detail {
    border-top: 1px solid currentColor;
}

.rate-limit-detail>span {
    font-size: 11px;
    letter-spacing: 0.1em;
}

.rate-limit-detail p {
    max-width: 400px;
    margin: 0;
    font-size: 13px;
    line-height: 1.8;
    opacity: 0.65;
}


.performance-note {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 48px;
    margin-top: 72px;
    padding: 32px 0;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.performance-note>span {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.performance-note p {
    max-width: 720px;
    margin: 0;
    font-size: clamp(17px, 1.8vw, 23px);
    line-height: 1.6;
    letter-spacing: -0.02em;
}


@media (max-width: 900px) {
    .performance-section {
        padding: 80px 0;
    }

    .performance-intro {
        grid-template-columns: 1fr;
        gap: 32px;
    }

    .performance-features {
        gap: 24px;
    }

    .rate-limit-main {
        padding: 30px;
    }

    .rate-limit-detail {
        padding: 28px;
    }
}

@media (max-width: 600px) {
    .performance-section {
        padding: 64px 0;
    }

    .performance-intro {
        margin-bottom: 48px;
    }

    .performance-intro h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .performance-intro>p {
        font-size: 14px;
    }

    .performance-diagram-header,
    .performance-diagram-footer {
        padding: 14px;
        font-size: 9px;
    }

    .cache-flow {
        padding: 32px 14px;
    }

    .cache-entry strong {
        font-size: 19px;
    }

    .cache-paths {
        gap: 10px;
    }

    .cache-result {
        padding: 14px 8px;
    }

    .cache-result strong {
        font-size: 15px;
    }

    .cache-result small {
        font-size: 10px;
    }

    .performance-features {
        grid-template-columns: 1fr;
        gap: 36px;
        margin-top: 64px;
    }

    .performance-feature h3 {
        margin-top: 22px;
    }

    .rate-limit-panel {
        grid-template-columns: 1fr;
        margin-top: 64px;
    }

    .rate-limit-main {
        gap: 40px;
        padding: 32px 24px;
    }

    .rate-limit-value strong {
        font-size: 112px;
    }

    .rate-limit-detail {
        padding: 28px 24px;
    }

    .performance-note {
        grid-template-columns: 1fr;
        gap: 20px;
        margin-top: 56px;
    }
}


.testing-section {
    padding: 112px 0;
    border-top: 1px solid currentColor;
}

.testing-intro {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: end;
    margin-bottom: 72px;
}

.testing-intro h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.testing-intro>p {
    max-width: 540px;
    margin: 0;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}


.testing-stats {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.testing-stat {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    min-width: 0;
    padding: 36px 32px;
}

.testing-stat:first-child {
    padding-left: 0;
}

.testing-stat+.testing-stat {
    border-left: 1px solid currentColor;
}

.testing-stat-label,
.testing-stat-caption {
    font-size: 10px;
    line-height: 1.6;
    letter-spacing: 0.1em;
}

.testing-stat-label {
    opacity: 0.55;
}

.testing-stat>strong {
    display: flex;
    align-items: center;
    gap: 14px;
    min-height: 100px;
    font-size: clamp(54px, 7vw, 100px);
    line-height: 1;
    letter-spacing: -0.07em;
    font-weight: 500;
}

.stat-unit {
    font-size: 0.5em;
}

.testing-stat-caption {
    max-width: 250px;
    opacity: 0.65;
}

.testing-stat>.ci-status {
    font-size: clamp(28px, 3.5vw, 48px);
    letter-spacing: -0.05em;
}

.ci-status-dot {
    width: 10px;
    height: 10px;
    flex-shrink: 0;
    border-radius: 50%;
    background: currentColor;
}


.testing-content {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 80px;
    margin-top: 96px;
}

.testing-column {
    min-width: 0;
}

.testing-column-label {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.testing-column h3 {
    margin: 32px 0 18px;
    font-size: clamp(28px, 3.2vw, 42px);
    line-height: 1.15;
    letter-spacing: -0.045em;
    font-weight: 500;
}

.testing-column>p {
    max-width: 480px;
    margin: 0 0 40px;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}


.test-categories {
    border-top: 1px solid currentColor;
}

.test-category {
    display: grid;
    grid-template-columns: 36px minmax(0, 1fr);
    gap: 16px;
    padding: 22px 0;
    border-bottom: 1px solid currentColor;
}

.test-category>span {
    font-size: 11px;
    opacity: 0.5;
}

.test-category h4 {
    margin: 0 0 8px;
    font-size: 16px;
    font-weight: 500;
}

.test-category p {
    margin: 0;
    font-size: 12px;
    line-height: 1.7;
    opacity: 0.65;
}


.ci-pipeline {
    border: 1px solid currentColor;
}

.ci-step {
    display: grid;
    grid-template-columns: 32px minmax(0, 1fr) 24px;
    align-items: center;
    gap: 14px;
    padding: 22px 20px;
}

.ci-step+.ci-step {
    border-top: 1px solid currentColor;
}

.ci-step-number {
    font-size: 11px;
    opacity: 0.5;
}

.ci-step>div {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.ci-step strong {
    font-size: 14px;
    font-weight: 500;
}

.ci-step small {
    font-size: 11px;
    line-height: 1.6;
    opacity: 0.6;
}

.ci-step-check {
    font-size: 17px;
    text-align: right;
}


.testing-note {
    display: grid;
    grid-template-columns: 1fr 2fr;
    gap: 48px;
    margin-top: 88px;
    padding: 32px 0;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.testing-note>span {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.testing-note p {
    max-width: 720px;
    margin: 0;
    font-size: clamp(17px, 1.8vw, 23px);
    line-height: 1.6;
    letter-spacing: -0.02em;
}


@media (max-width: 900px) {
    .testing-section {
        padding: 80px 0;
    }

    .testing-intro {
        grid-template-columns: 1fr;
        gap: 32px;
    }

    .testing-content {
        gap: 40px;
    }

    .testing-stat {
        padding: 28px 20px;
    }

    .testing-stat:first-child {
        padding-left: 0;
    }
}

@media (max-width: 600px) {
    .testing-section {
        padding: 64px 0;
    }

    .testing-intro {
        margin-bottom: 48px;
    }

    .testing-intro h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .testing-intro>p {
        font-size: 14px;
    }

    .testing-stats {
        grid-template-columns: 1fr;
    }

    .testing-stat,
    .testing-stat:first-child {
        padding: 26px 0;
    }

    .testing-stat+.testing-stat {
        border-left: 0;
        border-top: 1px solid currentColor;
    }

    .testing-stat>strong {
        min-height: 80px;
        font-size: 72px;
    }

    .testing-stat>.ci-status {
        font-size: 42px;
    }

    .testing-content {
        grid-template-columns: 1fr;
        gap: 72px;
        margin-top: 72px;
    }

    .testing-column h3 {
        margin-top: 24px;
    }

    .testing-note {
        grid-template-columns: 1fr;
        gap: 20px;
        margin-top: 64px;
    }
}


.conclusion-section {
    padding: 112px 0 120px;
    border-top: 1px solid currentColor;
}

.conclusion-layout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
}

.conclusion-heading h2 {
    margin: 0;
    font-size: clamp(44px, 5.5vw, 84px);
    line-height: 1.04;
    letter-spacing: -0.055em;
    font-weight: 500;
}

.conclusion-content {
    max-width: 560px;
}

.conclusion-content p {
    margin: 0 0 24px;
    font-size: 15px;
    line-height: 1.9;
    opacity: 0.65;
}

.conclusion-content .conclusion-lead {
    margin-bottom: 32px;
    font-size: clamp(19px, 2vw, 25px);
    line-height: 1.5;
    opacity: 1;
}


.conclusion-takeaways {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 40px;
    margin-top: 96px;
}

.takeaway {
    padding-top: 24px;
    border-top: 1px solid currentColor;
}

.takeaway-number {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.takeaway h3 {
    margin: 32px 0 18px;
    font-size: clamp(22px, 2.5vw, 32px);
    line-height: 1.2;
    letter-spacing: -0.04em;
    font-weight: 500;
}

.takeaway p {
    max-width: 390px;
    margin: 0;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}


.conclusion-footer {
    display: flex;
    justify-content: space-between;
    align-items: end;
    gap: 48px;
    margin-top: 112px;
    padding: 48px 0;
    border-top: 1px solid currentColor;
    border-bottom: 1px solid currentColor;
}

.conclusion-footer-copy>span {
    font-size: 10px;
    letter-spacing: 0.12em;
    opacity: 0.5;
}

.conclusion-footer-copy h3 {
    margin: 24px 0 16px;
    font-size: clamp(30px, 4vw, 54px);
    line-height: 1.1;
    letter-spacing: -0.05em;
    font-weight: 500;
}

.conclusion-footer-copy p {
    max-width: 470px;
    margin: 0;
    font-size: 13px;
    line-height: 1.9;
    opacity: 0.65;
}

.conclusion-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
}

.conclusion-source-link,
.conclusion-back-link {
    display: inline-flex;
    align-items: center;
    justify-content: space-between;
    gap: 32px;
    padding: 16px 20px;
    border: 1px solid currentColor;
    color: inherit;
    text-decoration: none;
    font-size: 11px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: background 0.2s, color 0.2s;
}

.conclusion-source-link {
    background: #111;
    color: #fff;
}

.conclusion-source-link:hover {
    background: #333;
}

.conclusion-back-link:hover {
    background: #111;
    color: #fff;
}


@media (max-width: 900px) {
    .conclusion-section {
        padding: 80px 0 96px;
    }

    .conclusion-layout {
        grid-template-columns: 1fr;
        gap: 40px;
    }

    .conclusion-takeaways {
        gap: 24px;
        margin-top: 72px;
    }

    .conclusion-footer {
        align-items: flex-start;
        flex-direction: column;
        margin-top: 88px;
    }
}

@media (max-width: 600px) {
    .conclusion-section {
        padding: 64px 0 80px;
    }

    .conclusion-heading h2 {
        font-size: clamp(42px, 11vw, 64px);
    }

    .conclusion-content p {
        font-size: 14px;
    }

    .conclusion-content .conclusion-lead {
        font-size: 19px;
    }

    .conclusion-takeaways {
        grid-template-columns: 1fr;
        gap: 36px;
        margin-top: 64px;
    }

    .takeaway h3 {
        margin-top: 22px;
    }

    .conclusion-footer {
        margin-top: 72px;
        padding: 36px 0;
    }

    .conclusion-actions {
        flex-direction: column;
        width: 100%;
    }

    .conclusion-source-link,
    .conclusion-back-link {
        width: 100%;
    }
}
</style>