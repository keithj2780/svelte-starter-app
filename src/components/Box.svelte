<div class="box {style}">
    <slot></slot>
</div>

<script>
    export let style="";
</script>

<style>
    .box {
        background-color: var(--componentbgcolor);
        border-radius: 4px;
        box-shadow: 0 2px 3px #111, 0 0 0 1px #111;
        display: block;
        padding: 1.25rem;
    }

    .box:hover, .box:focus {
        box-shadow: 0 3px 4px #222, 0 0 1px 1px #222;
    }
    .box:hover:active {
        box-shadow: 0 4px 3px #222, 0 0 0 1px #222;
    }

</style>