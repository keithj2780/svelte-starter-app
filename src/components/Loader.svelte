{#if modal}
<div class="{modalClass} {hidden}" {style}>
    <div class="loader centered {hidden}" {style}>
    </div>
</div>
{:else}
<div class="loader {hidden}" {style}>
</div>
{/if}

<script>
    import {onMount, createEventDispatcher} from 'svelte';

    export let style;
    export let timeout=0;
    export let hidden;
    export let modal;
    let modalClass;

	const dispatch = createEventDispatcher();

    onMount(() => {
        hidden="";
        modalClass="";
    });
    export function hide() {
        hidden='hide';
        modalClass="";
    }
    export function show() {
        hidden="";
        if (modal) modalClass="overlay";
        else       modalClass="";

        console.log('timeout='+timeout);
        console.log('modalClass='+modalClass);
        if (timeout > 0) 
            setTimeout(function(){ hide(); dispatch('close',{}); }, timeout);
    }
</script>
<style>
.hide {
    display:none;
}

.loader {
  border: 8px solid #f3f3f3; /* Light grey */
  border-top: 8px solid #3498db; /* Blue */
  border-radius: 50%;
  width: 24px;
  height: 24px;
  animation: spin 2s linear infinite;
}

.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%,-50%);
  transform: translate(-50%,-50%);

}
.overlay {
  position: fixed; /* Sit on top of the page content */
  width: 100%; /* Full width (cover the whole page) */
  height: 100%; /* Full height (cover the whole page) */
  top: 0; 
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0,0,0,0.5); /* Black background with opacity */
  z-index: 2; /* Specify a stack order in case you're using a different order for other elements */
  cursor: pointer; /* Add a pointer on hover */
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
