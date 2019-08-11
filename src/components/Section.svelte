<div class="section" {style}>
    <slot></slot>
</div>

<script>
    export let style="";
</script>

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