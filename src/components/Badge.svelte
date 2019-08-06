<div class="badge" {style}>
    <slot></slot>
</div>

<script>
  export let style;
</script>

<style>
:global(.badgeContainer) {
  position: relative;
  display: inline-block;
}

:global(.badgeContainer .badge) {
    position: absolute;
    top: -13px;
    right: -10px;
    padding: 5px 10px;
    border-radius: 50%;
    z-index:1;
}
</style>