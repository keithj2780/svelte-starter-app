<div class="slidecontainer">
    <input type="range" min={min} max={max} bind:value={value} class="slider" on:input={(e)=>handleChange(e)}>
</div>

<script>
  import { createEventDispatcher, onMount } from 'svelte';
 
  const dispatch = createEventDispatcher();
  export let value=50;
  export let min="1";
  export let max="100";

  function handleChange(e) {
    //console.log(e);
    //console.log(value);
    dispatch('change',value);
  }
</script>
<style>
.slidecontainer {
  width: 100%;
}

/* The slider itself */
.slider {
  -webkit-appearance: none;
  width: 101px;
  height: 14px;
  background: #7ab5db;
  color: #47525c;
  outline: none;
  border-radius: 5px;   
  opacity: 0.45;
  display: inline-block;
}

/* Mouse-over effects */
.slider:hover {
  opacity: 0.8;
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 12px;
  height: 12px;
  border-radius: 50%; 
  background: rgb(17, 19, 17);
  cursor: pointer;
}

.slider::-moz-range-thumb {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgb(17, 19, 17);
  cursor: pointer;
}
</style>