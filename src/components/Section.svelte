<div class="section">
    <slot></slot>
</div>

<style>
    :root {
        --section-padding: 2rem 1.5rem;
        --section-padding-medium: 9rem 1.5rem;
        --section-padding-large: 18rem 1.5rem;
    }

    .section {
        padding: var(--section-padding);
    }
</style>