<button class="collapsible {bShowContent?'minusIcon':''}" on:click|preventDefault="{() => bShowContent = !bShowContent}">
    {header}
</button>
{#if bShowContent}
<div    class="content" transition:scale="{{duration: 500, delay: 50, opacity: 0.2, start: 0.1}}">
  <slot></slot>
</div>
{/if}

<script>
    import { scale } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

    export let bShowContent = false;
    export let header = "";
</script>

<style>
/* Style the button that is used to open and close the collapsible content */
.collapsible {
  background-color: var(--navbackground);
  color: #444;
  cursor: pointer;
  padding: 16px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
}

/* Add a background color to the button if it is clicked on (add the .active class with JS), and when you move the mouse over it (hover) */
.active, .collapsible:hover {
  background-color: var(--navbackgroundhover);
}

.content {
  padding: 0 18px;
  background-color: white;
  max-height: 0;
  overflow: hidden;
  display:block;
  max-height: 100%;
}

.collapsible:after {
  content: '\02795'; /* "plus" sign (+) */
  font-size: 13px;
  color: white;
  float: right;
  margin-left: 5px;
}

.minusIcon:after {
  content: "\2796"; /* "minus" sign (-) */
}
</style>
