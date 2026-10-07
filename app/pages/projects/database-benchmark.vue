<script setup lang="ts">
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
                        University Project · Database Benchmarking
                    </p>

                    <h1>
                        PostgreSQL<br>
                        vs Redis
                    </h1>

                    <p class="hero-type">
                        Database Performance Benchmark
                    </p>

                    <p class="hero-description">
                        An individual university project comparing PostgreSQL and Redis
                        across a range of workloads to examine how their different
                        architectures affect throughput and response time.
                    </p>

                    <p class="hero-tools">
                        Python · PostgreSQL · Redis · Docker
                    </p>
                </div>

                <div class="hero-visual" aria-hidden="true">
                    <div class="database postgres">
                        <span class="database-name">PostgreSQL</span>
                        <span class="database-type">Relational Database</span>
                    </div>

                    <div class="connection">
                        <span></span>
                        <p>Benchmark</p>
                        <span></span>
                    </div>

                    <div class="database redis">
                        <span class="database-name">Redis</span>
                        <span class="database-type">In-Memory Data Store</span>
                    </div>
                </div>
            </div>
        </section>
        <section class="overview">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">
                        01 / Overview
                    </p>

                    <h2>
                        Two databases.<br>
                        Different architectures.
                    </h2>
                </div>

                <div class="overview-grid">
                    <p class="overview-lead">
                        How do a relational database and an in-memory data store behave
                        under the same types of workload?
                    </p>

                    <div class="overview-copy">
                        <p>
                            Developed individually as a university assignment, this project
                            benchmarks PostgreSQL and Redis across several database workloads
                            and compares their throughput and response times.
                        </p>

                        <p>
                            I built the benchmarking system in Python, generated synthetic test
                            data for both databases, automated the experiments, processed the
                            collected measurements, and exported the results for analysis.
                            PostgreSQL and Redis were run in a containerized Docker environment.
                        </p>

                        <p>
                            The goal was not simply to determine which database was faster, but
                            to observe how two fundamentally different database technologies
                            behave as the workload changes.
                        </p>
                    </div>
                </div>

                <div class="overview-facts">
                    <div class="fact">
                        <span class="fact-label">Project</span>
                        <span class="fact-value">Individual University Assignment</span>
                    </div>

                    <div class="fact">
                        <span class="fact-label">Focus</span>
                        <span class="fact-value">Database Performance</span>
                    </div>

                    <div class="fact">
                        <span class="fact-label">Compared</span>
                        <span class="fact-value">PostgreSQL / Redis</span>
                    </div>

                    <div class="fact">
                        <span class="fact-label">Output</span>
                        <span class="fact-value">Automated Benchmark Results</span>
                    </div>
                </div>
            </div>
        </section>
        <section class="architecture">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">02 / Architecture</p>

                    <h2>
                        One benchmark.<br>
                        Two database systems.
                    </h2>
                </div>

                <div class="architecture-intro">
                    <p>
                        The benchmark was built as a containerized environment using Docker
                        Compose. A Python application handled data generation, benchmark
                        execution, measurement, and result processing while PostgreSQL and
                        Redis ran as separate services.
                    </p>
                </div>

                <div class="architecture-diagram">
                    <div class="architecture-node benchmark-node">
                        <span class="node-number">01</span>

                        <div>
                            <span class="node-label">Application</span>
                            <h3>Python Benchmark</h3>
                        </div>

                        <p>
                            Synthetic data · Workloads<br>
                            Timing · Result processing
                        </p>
                    </div>

                    <div class="architecture-branches" aria-hidden="true">
                        <div class="branch branch-left"></div>
                        <span>Docker Compose</span>
                        <div class="branch branch-right"></div>
                    </div>

                    <div class="database-nodes">
                        <div class="architecture-node">
                            <span class="node-number">02</span>

                            <div>
                                <span class="node-label">Database</span>
                                <h3>PostgreSQL</h3>
                            </div>

                            <p>
                                Relational storage<br>
                                SQL queries · Transactions
                            </p>
                        </div>

                        <div class="architecture-node">
                            <span class="node-number">03</span>

                            <div>
                                <span class="node-label">Data Store</span>
                                <h3>Redis</h3>
                            </div>

                            <p>
                                In-memory storage<br>
                                Key-value access
                            </p>
                        </div>
                    </div>
                </div>

                <div class="pipeline">
                    <div class="pipeline-step">
                        <span>01</span>
                        <p>Generate synthetic user data</p>
                    </div>

                    <div class="pipeline-arrow" aria-hidden="true">→</div>

                    <div class="pipeline-step">
                        <span>02</span>
                        <p>Populate both databases</p>
                    </div>

                    <div class="pipeline-arrow" aria-hidden="true">→</div>

                    <div class="pipeline-step">
                        <span>03</span>
                        <p>Execute benchmark workloads</p>
                    </div>

                    <div class="pipeline-arrow" aria-hidden="true">→</div>

                    <div class="pipeline-step">
                        <span>04</span>
                        <p>Collect performance metrics</p>
                    </div>

                    <div class="pipeline-arrow" aria-hidden="true">→</div>

                    <div class="pipeline-step">
                        <span>05</span>
                        <p>Process and export results</p>
                    </div>
                </div>

                <p class="architecture-caption">
                    Faker generated the synthetic dataset, Pandas processed the collected
                    measurements, and OpenPyXL was used to export the benchmark results to
                    an Excel workbook.
                </p>
            </div>
        </section>
        <section class="benchmark-design">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">03 / Benchmark Design</p>

                    <h2>
                        Testing different<br>
                        workload patterns.
                    </h2>
                </div>

                <div class="benchmark-intro">
                    <p>
                        The benchmark used multiple scenarios rather than relying on a single
                        performance test. Each scenario focused on a different workload
                        characteristic, from basic reads and writes to concurrent operations
                        and transaction-heavy workloads.
                    </p>
                </div>

                <div class="benchmark-grid">
                    <article class="benchmark-card">
                        <span class="benchmark-number">01</span>

                        <div>
                            <h3>Read / Write</h3>
                            <p>
                                Compared throughput under different combinations of read and
                                write operations.
                            </p>
                        </div>

                        <span class="benchmark-metric">Operations / second</span>
                    </article>

                    <article class="benchmark-card">
                        <span class="benchmark-number">02</span>

                        <div>
                            <h3>Key Access</h3>
                            <p>
                                Measured response times when records were accessed at different
                                frequencies.
                            </p>
                        </div>

                        <span class="benchmark-metric">Response time</span>
                    </article>

                    <article class="benchmark-card">
                        <span class="benchmark-number">03</span>

                        <div>
                            <h3>Row Load</h3>
                            <p>
                                Examined how query response time changed as different amounts of
                                data were retrieved.
                            </p>
                        </div>

                        <span class="benchmark-metric">Query time</span>
                    </article>

                    <article class="benchmark-card">
                        <span class="benchmark-number">04</span>

                        <div>
                            <h3>Concurrency</h3>
                            <p>
                                Executed database operations concurrently to measure behavior
                                under simultaneous workloads.
                            </p>
                        </div>

                        <span class="benchmark-metric">Execution time</span>
                    </article>

                    <article class="benchmark-card">
                        <span class="benchmark-number">05</span>

                        <div>
                            <h3>Read-Heavy</h3>
                            <p>
                                Simulated workloads dominated by database read operations.
                            </p>
                        </div>

                        <span class="benchmark-metric">Transaction time</span>
                    </article>

                    <article class="benchmark-card">
                        <span class="benchmark-number">06</span>

                        <div>
                            <h3>Write-Heavy</h3>
                            <p>
                                Simulated workloads dominated by database write operations.
                            </p>
                        </div>

                        <span class="benchmark-metric">Transaction time</span>
                    </article>

                    <article class="benchmark-card benchmark-card-wide">
                        <span class="benchmark-number">07</span>

                        <div>
                            <h3>Transactional Operations</h3>
                            <p>
                                Combined read, insert, and update operations to examine more
                                complex database interaction patterns.
                            </p>
                        </div>

                        <span class="benchmark-metric">Combined workload</span>
                    </article>
                </div>
            </div>
        </section>
        <section class="measurement">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">04 / Measurement & Automation</p>

                    <h2>
                        From operation<br>
                        to measurable result.
                    </h2>
                </div>

                <div class="measurement-intro">
                    <p>
                        The benchmarking process was automated in Python. Each scenario
                        executed database operations, measured their execution time, repeated
                        the experiment across multiple iterations, and collected the results
                        for processing and comparison.
                    </p>
                </div>

                <div class="measurement-flow">
                    <div class="flow-step">
                        <span class="flow-number">01</span>
                        <span class="flow-label">Workload</span>
                        <h3>Execute</h3>
                        <p>Run the selected database operation or workload scenario.</p>
                    </div>

                    <div class="flow-connector" aria-hidden="true">→</div>

                    <div class="flow-step">
                        <span class="flow-number">02</span>
                        <span class="flow-label">Timing</span>
                        <h3>Measure</h3>
                        <p>Capture execution time and calculate throughput where applicable.</p>
                    </div>

                    <div class="flow-connector" aria-hidden="true">→</div>

                    <div class="flow-step">
                        <span class="flow-number">03</span>
                        <span class="flow-label">Iterations</span>
                        <h3>Repeat</h3>
                        <p>Repeat the benchmark to produce a larger measurement set.</p>
                    </div>

                    <div class="flow-connector" aria-hidden="true">→</div>

                    <div class="flow-step">
                        <span class="flow-number">04</span>
                        <span class="flow-label">Analysis</span>
                        <h3>Aggregate</h3>
                        <p>Calculate averages and medians from the collected results.</p>
                    </div>

                    <div class="flow-connector" aria-hidden="true">→</div>

                    <div class="flow-step">
                        <span class="flow-number">05</span>
                        <span class="flow-label">Output</span>
                        <h3>Export</h3>
                        <p>Write the processed benchmark data to an Excel workbook.</p>
                    </div>
                </div>

                <div class="measurement-details">
                    <div class="detail-block">
                        <span class="detail-label">Iterations</span>
                        <strong>100</strong>
                        <p>
                            Benchmark scenarios were repeatedly executed to collect multiple
                            measurements rather than relying on a single run.
                        </p>
                    </div>

                    <div class="detail-block">
                        <span class="detail-label">Concurrency</span>
                        <strong>ThreadPoolExecutor</strong>
                        <p>
                            Concurrent workloads were executed using Python worker threads to
                            simulate simultaneous database operations.
                        </p>
                    </div>

                    <div class="detail-block">
                        <span class="detail-label">Processing</span>
                        <strong>Pandas</strong>
                        <p>
                            Collected measurements were organized and processed to calculate
                            summary statistics for comparison.
                        </p>
                    </div>

                    <div class="detail-block">
                        <span class="detail-label">Reporting</span>
                        <strong>Excel</strong>
                        <p>
                            Results were automatically exported into separate worksheets for
                            the different benchmark scenarios.
                        </p>
                    </div>
                </div>
            </div>
        </section>
        <section class="results">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">05 / Results</p>

                    <h2>
                        Different architectures.<br>
                        Different performance.
                    </h2>
                </div>

                <div class="results-intro">
                    <p>
                        Across the tested workloads, Redis generally maintained higher
                        throughput and lower response times, while PostgreSQL showed a more
                        pronounced performance decrease as the benchmark workload increased.
                    </p>
                </div>

                <div class="result-feature">
                    <div class="result-heading">
                        <div>
                            <span class="result-number">01</span>
                            <h3>Read Throughput</h3>
                        </div>

                        <p>
                            Redis maintained comparatively high read throughput across the
                            benchmark, while PostgreSQL throughput decreased substantially as
                            the number of operations increased.
                        </p>
                    </div>

                    <EnlargeableImage src="/images/database-benchmark/read-throughput.png"
                        alt="Benchmark graph comparing Redis and PostgreSQL average read throughput"
                        @enlarge="openLightbox" />
                </div>

                <div class="result-feature">
                    <div class="result-heading">
                        <div>
                            <span class="result-number">02</span>
                            <h3>Write Throughput</h3>
                        </div>

                        <p>
                            Redis write throughput fluctuated between runs but remained
                            comparatively stable, while PostgreSQL showed a declining
                            throughput trend in the tested write workload.
                        </p>
                    </div>

                    <EnlargeableImage src="/images/database-benchmark/write-throughput.png"
                        alt="Benchmark graph comparing Redis and PostgreSQL average write throughput"
                        @enlarge="openLightbox" />
                </div>

                <div class="result-pair">
                    <article class="result-small">
                        <div class="result-small-heading">
                            <span class="result-number">03</span>
                            <h3>Key Access</h3>
                        </div>

                        <EnlargeableImage src="/images/database-benchmark/key-access.png"
                            alt="Benchmark graph comparing Redis and PostgreSQL key access response time"
                            @enlarge="openLightbox" />

                        <p>
                            Response time increased for both systems, but the increase was more
                            pronounced for PostgreSQL in this benchmark.
                        </p>
                    </article>

                    <article class="result-small">
                        <div class="result-small-heading">
                            <span class="result-number">04</span>
                            <h3>Concurrency</h3>
                        </div>

                        <EnlargeableImage src="/images/database-benchmark/concurrent-time.png"
                            alt="Benchmark graph comparing Redis and PostgreSQL concurrent operation time"
                            @enlarge="openLightbox" />

                        <p>
                            Redis produced lower concurrent execution times overall, while
                            PostgreSQL showed greater fluctuation as the workload progressed.
                        </p>
                    </article>
                </div>

                <div class="result-pair">
                    <article class="result-small">
                        <div class="result-small-heading">
                            <span class="result-number">05</span>
                            <h3>Read-Heavy</h3>
                        </div>

                        <EnlargeableImage src="/images/database-benchmark/read-heavy.png"
                            alt="Benchmark graph comparing Redis and PostgreSQL read-heavy transaction time"
                            @enlarge="openLightbox" />

                        <p>
                            Transaction time increased for both databases, with PostgreSQL
                            showing a somewhat steeper increase in the tested workload.
                        </p>
                    </article>

                    <article class="result-small">
                        <div class="result-small-heading">
                            <span class="result-number">06</span>
                            <h3>Write-Heavy</h3>
                        </div>

                        <EnlargeableImage src="/images/database-benchmark/write-heavy.png"
                            alt="Benchmark graph comparing Redis and PostgreSQL write-heavy transaction time"
                            @enlarge="openLightbox" />

                        <p>
                            Both systems required more time as the write-heavy workload
                            increased, with PostgreSQL showing the more consistent upward trend.
                        </p>
                    </article>
                </div>

                <div class="result-summary">
                    <span class="result-summary-label">Overall observation</span>

                    <p>
                        Within this benchmark environment, Redis generally delivered higher
                        throughput and lower response times than PostgreSQL. These results
                        describe the tested workloads rather than establishing one database
                        as universally better than the other.
                    </p>
                </div>
            </div>
        </section>
        <section class="conclusion">
            <div class="container">
                <div class="section-intro">
                    <p class="section-label">06 / Conclusion</p>

                    <h2>
                        Performance is only<br>
                        part of the decision.
                    </h2>
                </div>

                <div class="conclusion-grid">
                    <div class="conclusion-lead">
                        <p>
                            Redis performed better across many of the workloads tested in this
                            project, but raw performance alone does not determine which database
                            is appropriate for an application.
                        </p>
                    </div>

                    <div class="conclusion-copy">
                        <p>
                            Redis demonstrated the advantages of fast in-memory access,
                            particularly in workloads involving frequent access and concurrent
                            operations.
                        </p>

                        <p>
                            PostgreSQL provides capabilities that serve different requirements,
                            including relational data modeling, SQL querying, structured
                            transactions, and persistent storage.
                        </p>

                        <p>
                            The project reinforced that database selection should be based on
                            the application's data model, workload, persistence requirements,
                            query complexity, and transactional needs rather than benchmark
                            performance in isolation.
                        </p>
                    </div>
                </div>

                <div class="takeaways">
                    <div class="takeaway">
                        <span>01</span>
                        <p>Design benchmarks around multiple workload characteristics.</p>
                    </div>

                    <div class="takeaway">
                        <span>02</span>
                        <p>Automate repeated measurements and result processing.</p>
                    </div>

                    <div class="takeaway">
                        <span>03</span>
                        <p>Interpret performance results in the context of system design.</p>
                    </div>
                </div>

                <div class="project-links">
                    <a href="https://github.com/DujeVidas/Database_Benchmark_Redis_PostgreSQL" target="_blank"
                        rel="noopener noreferrer">
                        <span>View Source</span>
                        <span aria-hidden="true">↗</span>
                    </a>

                    <a href="/documents/database-benchmark-report.pdf" target="_blank">
                        <span>View Full Report</span>
                        <span aria-hidden="true">↗</span>
                    </a>
                </div>
            </div>
        </section>

        <section class="project-end">
            <div class="container">
                <NuxtLink to="/" class="back-link">
                    <span aria-hidden="true">←</span>
                    <span>Back to all work</span>
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
    grid-template-columns: minmax(0, 1fr) minmax(420px, 0.8fr);
    align-items: center;
    gap: clamp(64px, 8vw, 140px);
}

.hero-content {
    max-width: 720px;
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
    line-height: 0.86;
    letter-spacing: -0.055em;

    text-transform: uppercase;
}

.hero-type {
    margin: 28px 0 0;

    font-size: 1rem;
    font-weight: 500;
}

.hero-description {
    max-width: 590px;
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
    display: flex;
    flex-direction: column;

    width: 100%;

    border: 1px solid var(--color-border);
}

.database {
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    min-height: 190px;
    padding: 28px;

    background: var(--color-surface);
}

.database-name {
    font-size: clamp(1.8rem, 3vw, 3rem);
    font-weight: 500;
    letter-spacing: -0.035em;
}

.database-type {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.connection {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: 16px;

    padding: 16px 28px;

    border-block: 1px solid var(--color-border);
}

.connection span {
    height: 1px;

    background: var(--color-border);
}

.connection p {
    margin: 0;

    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
}

.redis {
    text-align: right;
}

@media (max-width: 1000px) {
    .project-hero {
        min-height: auto;
    }

    .hero-grid {
        grid-template-columns: 1fr;
        gap: 72px;
    }

    .hero-content {
        max-width: 760px;
    }

    .hero-visual {
        max-width: 700px;
    }
}

@media (max-width: 768px) {
    .project-hero {
        padding-block: 64px 80px;
    }

    h1 {
        font-size: clamp(3.7rem, 17vw, 6.5rem);
    }

    .hero-grid {
        gap: 56px;
    }

    .database {
        min-height: 150px;
        padding: 22px;
    }

    .connection {
        padding-inline: 22px;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: clamp(3.2rem, 16vw, 5rem);
    }
}

.overview {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.section-intro {
    margin-bottom: 96px;
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
    max-width: 900px;
    margin: 0;

    font-size: clamp(2.8rem, 5vw, 5.5rem);
    font-weight: 500;
    line-height: 1;
    letter-spacing: -0.045em;
}

.overview-grid {
    display: grid;
    grid-template-columns: minmax(0, 0.8fr) minmax(0, 1fr);
    gap: clamp(64px, 10vw, 180px);

    margin-bottom: 120px;
}

.overview-lead {
    max-width: 520px;
    margin: 0;

    font-size: clamp(1.6rem, 2.5vw, 2.6rem);
    line-height: 1.3;
    letter-spacing: -0.025em;
}

.overview-copy {
    max-width: 650px;
}

.overview-copy p {
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.overview-copy p+p {
    margin-top: 28px;
}

.overview-facts {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));

    border-top: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.fact {
    display: flex;
    flex-direction: column;
    gap: 28px;

    min-width: 0;
    padding: 28px;
}

.fact+.fact {
    border-left: 1px solid var(--color-border);
}

.fact-label {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    font-weight: 500;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.fact-value {
    margin-top: auto;

    font-size: 0.9rem;
    line-height: 1.5;
}

@media (max-width: 900px) {
    .overview-facts {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .fact:nth-child(3) {
        border-left: 0;
    }

    .fact:nth-child(n + 3) {
        border-top: 1px solid var(--color-border);
    }
}

@media (max-width: 768px) {
    .overview {
        padding-block: 96px;
    }

    .section-intro {
        margin-bottom: 64px;
    }

    .overview-grid {
        grid-template-columns: 1fr;
        gap: 48px;

        margin-bottom: 80px;
    }
}

@media (max-width: 520px) {
    .overview-facts {
        grid-template-columns: 1fr;
    }

    .fact+.fact {
        border-top: 1px solid var(--color-border);
        border-left: 0;
    }
}

.architecture {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.architecture-intro {
    display: flex;
    justify-content: flex-end;

    margin-bottom: 96px;
}

.architecture-intro p {
    max-width: 650px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.architecture-diagram {
    max-width: 1050px;
    margin-inline: auto;
    margin-bottom: 120px;
}

.architecture-node {
    position: relative;

    display: flex;
    flex-direction: column;
    justify-content: space-between;

    min-height: 260px;
    padding: 28px;

    border: 1px solid var(--color-border);
    background: var(--color-surface);
}

.benchmark-node {
    width: calc(50% - 16px);
    margin-inline: auto;
}

.node-number {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
}

.node-label {
    display: block;

    margin-bottom: 8px;

    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.architecture-node h3 {
    margin: 0;

    font-size: clamp(1.7rem, 2.5vw, 2.6rem);
    font-weight: 500;
    letter-spacing: -0.035em;
}

.architecture-node p {
    margin: 0;

    color: var(--color-text-muted);

    font-size: 0.75rem;
    line-height: 1.7;
    text-transform: uppercase;
    letter-spacing: 0.06em;
}

.architecture-branches {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    gap: 20px;

    height: 100px;
}

.architecture-branches span {
    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
}

.branch {
    height: 1px;

    background: var(--color-border);
}

.database-nodes {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 32px;
}

.pipeline {
    display: grid;
    grid-template-columns:
        minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr);
    align-items: center;

    padding-block: 32px;

    border-top: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.pipeline-step {
    min-width: 0;
}

.pipeline-step span {
    display: block;

    margin-bottom: 20px;

    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.1em;
}

.pipeline-step p {
    margin: 0;

    font-size: 0.8rem;
    line-height: 1.5;
}

.pipeline-arrow {
    padding-inline: 18px;

    color: var(--color-text-muted);

    font-size: 0.8rem;
}

.architecture-caption {
    max-width: 680px;
    margin: 28px 0 0 auto;

    color: var(--color-text-muted);

    font-size: 0.75rem;
    line-height: 1.7;
}

@media (max-width: 900px) {
    .pipeline {
        grid-template-columns: 1fr;
        gap: 0;

        padding-block: 0;
    }

    .pipeline-step {
        display: grid;
        grid-template-columns: 50px 1fr;
        align-items: center;

        padding-block: 22px;
    }

    .pipeline-step+.pipeline-step {
        border-top: 1px solid var(--color-border);
    }

    .pipeline-step span {
        margin: 0;
    }

    .pipeline-arrow {
        display: none;
    }
}

@media (max-width: 768px) {
    .architecture {
        padding-block: 96px;
    }

    .architecture-intro {
        justify-content: flex-start;

        margin-bottom: 64px;
    }

    .architecture-diagram {
        margin-bottom: 80px;
    }

    .benchmark-node {
        width: 100%;
    }

    .architecture-branches {
        grid-template-columns: 1fr auto 1fr;

        height: 72px;
    }

    .database-nodes {
        grid-template-columns: 1fr;
        gap: 16px;
    }

    .architecture-node {
        min-height: 220px;
    }
}

.benchmark-design {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.benchmark-intro {
    display: flex;
    justify-content: flex-end;

    margin-bottom: 96px;
}

.benchmark-intro p {
    max-width: 650px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.benchmark-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));

    border-top: 1px solid var(--color-border);
    border-left: 1px solid var(--color-border);
}

.benchmark-card {
    display: grid;
    grid-template-rows: auto 1fr auto;
    gap: 52px;

    min-height: 340px;
    padding: 28px;

    border-right: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.benchmark-number {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
}

.benchmark-card h3 {
    margin: 0 0 16px;

    font-size: clamp(1.8rem, 3vw, 3rem);
    font-weight: 500;
    letter-spacing: -0.04em;
}

.benchmark-card p {
    max-width: 480px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 0.9rem;
    line-height: 1.7;
}

.benchmark-metric {
    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.benchmark-card-wide {
    grid-column: 1 / -1;

    min-height: 280px;
}

.benchmark-card-wide>div {
    max-width: 700px;
}

.benchmark-card {
    transition:
        background-color 180ms ease,
        transform 180ms ease;
}

@media (hover: hover) {
    .benchmark-card:hover {
        background: var(--color-surface);
    }
}

@media (max-width: 768px) {
    .benchmark-design {
        padding-block: 96px;
    }

    .benchmark-intro {
        justify-content: flex-start;

        margin-bottom: 64px;
    }

    .benchmark-grid {
        grid-template-columns: 1fr;
    }

    .benchmark-card,
    .benchmark-card-wide {
        grid-column: auto;

        min-height: 280px;
    }
}

.measurement {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.measurement-intro {
    display: flex;
    justify-content: flex-end;

    margin-bottom: 96px;
}

.measurement-intro p {
    max-width: 650px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.measurement-flow {
    display: grid;
    grid-template-columns:
        minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr) auto minmax(0, 1fr);
    align-items: stretch;

    margin-bottom: 120px;
}

.flow-step {
    display: flex;
    flex-direction: column;

    min-width: 0;
    min-height: 300px;
    padding: 24px;

    border: 1px solid var(--color-border);
}

.flow-number {
    margin-bottom: 52px;

    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.1em;
}

.flow-label {
    margin-bottom: 8px;

    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.flow-step h3 {
    margin: 0;

    font-size: clamp(1.5rem, 2vw, 2.2rem);
    font-weight: 500;
    letter-spacing: -0.035em;
}

.flow-step p {
    margin: auto 0 0;

    color: var(--color-text-muted);

    font-size: 0.75rem;
    line-height: 1.6;
}

.flow-connector {
    display: flex;
    align-items: center;

    padding-inline: 12px;

    color: var(--color-text-muted);
}

.measurement-details {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));

    border-top: 1px solid var(--color-border);
    border-left: 1px solid var(--color-border);
}

.detail-block {
    display: grid;
    grid-template-columns: 130px 1fr;
    gap: 20px 32px;

    padding: 32px;

    border-right: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.detail-label {
    color: var(--color-text-muted);

    font-size: 0.6rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.detail-block strong {
    font-size: 1rem;
    font-weight: 500;
}

.detail-block p {
    grid-column: 2;

    max-width: 430px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 0.8rem;
    line-height: 1.7;
}

@media (max-width: 1100px) {
    .measurement-flow {
        grid-template-columns: 1fr;
    }

    .flow-step {
        min-height: 220px;
    }

    .flow-connector {
        justify-content: center;

        height: 48px;
        padding: 0;

        transform: rotate(90deg);
    }
}

@media (max-width: 768px) {
    .measurement {
        padding-block: 96px;
    }

    .measurement-intro {
        justify-content: flex-start;

        margin-bottom: 64px;
    }

    .measurement-flow {
        margin-bottom: 80px;
    }

    .measurement-details {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 520px) {
    .detail-block {
        grid-template-columns: 1fr;
    }

    .detail-block p {
        grid-column: auto;
    }
}

.results {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.results-intro {
    display: flex;
    justify-content: flex-end;

    margin-bottom: 120px;
}

.results-intro p {
    max-width: 650px;
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.result-feature {
    padding-block: 72px;

    border-top: 1px solid var(--color-border);
}

.result-heading {
    display: grid;
    grid-template-columns: 1fr minmax(280px, 480px);
    gap: 64px;

    margin-bottom: 48px;
}

.result-number {
    display: block;

    margin-bottom: 16px;

    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
}

.result-heading h3,
.result-small-heading h3 {
    margin: 0;

    font-size: clamp(2rem, 3vw, 3.5rem);
    font-weight: 500;
    letter-spacing: -0.04em;
}

.result-heading>p {
    margin: 0;

    color: var(--color-text-muted);

    font-size: 0.9rem;
    line-height: 1.7;
}

.result-pair {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));

    border-top: 1px solid var(--color-border);
}

.result-small {
    min-width: 0;
    padding: 64px 0;
}

.result-small:first-child {
    padding-right: 48px;
}

.result-small+.result-small {
    padding-left: 48px;

    border-left: 1px solid var(--color-border);
}

.result-small-heading {
    margin-bottom: 40px;
}

.result-small>p {
    max-width: 500px;
    margin: 32px 0 0;

    color: var(--color-text-muted);

    font-size: 0.85rem;
    line-height: 1.7;
}

.result-summary {
    display: grid;
    grid-template-columns: minmax(160px, 0.4fr) minmax(0, 1fr);
    gap: 64px;

    padding: 64px 0;

    border-top: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.result-summary-label {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
}

.result-summary p {
    max-width: 850px;
    margin: 0;

    font-size: clamp(1.5rem, 2.5vw, 2.6rem);
    line-height: 1.35;
    letter-spacing: -0.025em;
}

@media (max-width: 768px) {
    .results {
        padding-block: 96px;
    }

    .results-intro {
        justify-content: flex-start;

        margin-bottom: 80px;
    }

    .result-heading {
        grid-template-columns: 1fr;
        gap: 28px;
    }

    .result-pair {
        grid-template-columns: 1fr;
    }

    .result-small:first-child,
    .result-small+.result-small {
        padding: 56px 0;
    }

    .result-small+.result-small {
        border-top: 1px solid var(--color-border);
        border-left: 0;
    }

    .result-summary {
        grid-template-columns: 1fr;
        gap: 32px;
    }
}

.conclusion {
    padding-block: 160px;

    border-top: 1px solid var(--color-border);
}

.conclusion-grid {
    display: grid;
    grid-template-columns: minmax(0, 0.8fr) minmax(0, 1fr);
    gap: clamp(64px, 10vw, 180px);

    margin-bottom: 120px;
}

.conclusion-lead p {
    max-width: 560px;
    margin: 0;

    font-size: clamp(1.6rem, 2.5vw, 2.6rem);
    line-height: 1.3;
    letter-spacing: -0.025em;
}

.conclusion-copy {
    max-width: 650px;
}

.conclusion-copy p {
    margin: 0;

    color: var(--color-text-muted);

    font-size: 1rem;
    line-height: 1.8;
}

.conclusion-copy p+p {
    margin-top: 28px;
}

.takeaways {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));

    margin-bottom: 96px;

    border-top: 1px solid var(--color-border);
    border-bottom: 1px solid var(--color-border);
}

.takeaway {
    display: flex;
    flex-direction: column;
    gap: 64px;

    min-height: 220px;
    padding: 28px;
}

.takeaway+.takeaway {
    border-left: 1px solid var(--color-border);
}

.takeaway span {
    color: var(--color-text-muted);

    font-size: 0.65rem;
    letter-spacing: 0.1em;
}

.takeaway p {
    max-width: 300px;
    margin: auto 0 0;

    font-size: 1rem;
    line-height: 1.5;
}

.project-links {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));

    border-top: 1px solid var(--color-border);
}

.project-links a {
    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 32px 0;

    color: inherit;

    font-size: clamp(1.2rem, 2vw, 1.8rem);
    text-decoration: none;

    transition: opacity 180ms ease;
}

.project-links a:first-child {
    padding-right: 32px;
}

.project-links a+a {
    padding-left: 32px;

    border-left: 1px solid var(--color-border);
}

.project-links a span:last-child {
    transition: transform 180ms ease;
}

@media (hover: hover) {
    .project-links a:hover span:last-child {
        transform: translate(4px, -4px);
    }
}

.project-end {
    padding-block: 48px;

    border-top: 1px solid var(--color-border);
}

.back-link {
    display: inline-flex;
    align-items: center;
    gap: 12px;

    color: inherit;

    font-size: 0.75rem;
    letter-spacing: 0.08em;
    text-decoration: none;
    text-transform: uppercase;
}

.back-link span:first-child {
    transition: transform 180ms ease;
}

@media (hover: hover) {
    .back-link:hover span:first-child {
        transform: translateX(-4px);
    }
}

@media (max-width: 768px) {
    .conclusion {
        padding-block: 96px;
    }

    .conclusion-grid {
        grid-template-columns: 1fr;
        gap: 48px;

        margin-bottom: 80px;
    }

    .takeaways {
        grid-template-columns: 1fr;

        margin-bottom: 72px;
    }

    .takeaway {
        min-height: 180px;
    }

    .takeaway+.takeaway {
        border-top: 1px solid var(--color-border);
        border-left: 0;
    }

    .project-links {
        grid-template-columns: 1fr;
    }

    .project-links a:first-child,
    .project-links a+a {
        padding: 28px 0;
    }

    .project-links a+a {
        border-top: 1px solid var(--color-border);
        border-left: 0;
    }
}
</style>