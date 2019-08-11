<div class="loader {hidden}" {style}>

</div>

<script>
    import {onMount, createEventDispatcher} from 'svelte';

    export let style;
    export let timeout;
    export let hidden;

	const dispatch = createEventDispatcher();

    onMount(() => {
        hidden="";
    });
    export function hide() {
        hidden='hide';
    }
    export function show() {
        hidden="";
        console.log('timeout='+timeout);
        if (timeout) 
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

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
