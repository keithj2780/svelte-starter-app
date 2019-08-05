<div class="badge">
    <slot></slot>
</div>
<style>
:global(.badgeContainer) {
  position: relative;
  display: inline-block;
}

:global(.badgeContainer .badge) {
    position: absolute;
    top: -10px;
    right: -10px;
    padding: 5px 10px;
    border-radius: 50%;
    background: rgb(163, 14, 14);
    color: white;
    z-index:1;
}
</style>