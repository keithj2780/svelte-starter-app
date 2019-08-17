<div class="badge" {style} on:click="{()=> dispatch('click')}">
    <slot></slot>
</div>

<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  export let style="";

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
    color:white;
    background-color: rgb(160, 47, 47);
    z-index:1;
}
</style>