<svg class="tick-icon">
    <symbol id="check-tick" viewbox="0 0 12 10">
        <polyline points="1.5 6 4.5 9 10.5 1"></polyline>
    </symbol>
</svg>

<input class="main" bind:checked={checked} id="cb{uid}" type="checkbox" style="display: none;"/>
<label class="inside-label" for="cb{uid}">
    <span>
        <svg width="12px" height="10px"><use xlink:href="#check-tick"></use></svg>
    </span>
    <span>{label}</span>
</label>

<script>
  import { onMount, createEventDispatcher } from 'svelte';

  export let label="";
  export let checked;
  let uid;

  const dispatch = createEventDispatcher();

  onMount(() => {
    uid=Math.floor(Math.random()*999999999999);     //  we need to generate unique ids, so a click on the label goes tothe right checkbox
  });

</script>

<style>
.inside-label {
  cursor: pointer;
  user-select: none;
  padding: 6px 8px;
  border-radius: 8px;
  overflow: hidden;
  transition: all 0.2s ease;
}
.inside-label:not(:last-child) {
  margin-right: 6px;
}
.inside-label:hover {
  background: var(--buttonbgcolorhover);
}
.inside-label span {
  float: left;
  vertical-align: middle;
  transform: translate3d(0, 0, 0);
  font-weight: 800;
}
.inside-label span:first-child {
  position: relative;
  width: 18px;
  height: 18px;
  border-radius: 4px;
  transform: scale(1);
  border: 2px solid #c8ccd4;
  transition: all 0.2s ease;
}
.inside-label span:first-child svg {
  position: absolute;
  top: 2px;
  left: 1px;
  fill: none;
  stroke: #fff;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-dasharray: 16px;
  stroke-dashoffset: 16px;
  transition: all 0.3s ease;
  transition-delay: 0.1s;
  transform: translate3d(0, 0, 0);
}
.inside-label span:last-child {
  padding-left: 8px;
  line-height: 18px;
}
.inside-label:hover span:first-child {
  border-color: var(--buttonbgcolor);
}
.main:checked + .inside-label span:first-child {
  background: var(--buttonbgcolor);
  border-color: var(--buttonbgcolor);
  animation: myAnimation 0.2s ease;
}
.main:checked + .inside-label span:first-child svg {
  stroke-dashoffset: 0;
}
 
.tick-icon {
  position: absolute;
  width: 0;
  height: 0;
  pointer-events: none;
  user-select: none;
}
@media screen and (max-width: 650px) {
	
  .inside-label {
      width: 100%;
      margin-bottom: 4px;
      display: inline-block;
  }
}
 
@keyframes myAnimation {
  50% {
    transform: scale(0.9);
  }
}
</style>