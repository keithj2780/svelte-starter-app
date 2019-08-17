{#if show}
<div class="snackbarshow" {style} in:fly="{{y:80, duration: 1000}}" out:fade>
    <slot>{text}</slot>
</div>
{/if}

<script>
	import { createEventDispatcher } from 'svelte';
	import { fade,fly } from 'svelte/transition';

    export let show=false;
    export let style="";
    export let text="";
    export let showMS = 3000;


	const dispatch = createEventDispatcher();

    export function showToast() {
        showMS = 6000;
        show = true;
        setTimeout(function(){ show = true; dispatch('close',{}); }, ms);
    }

    export function showToastForMS(ms) {
        show = true;
        showMS = ms+3000;
        // After 3 seconds, remove the show class from DIV
        setTimeout(function(){ show=false; dispatch('close',{}); }, ms);
    }

</script>

<style>
    /* The snackbar - position it at the bottom and in the middle of the screen */
    :global(.snackbar) {
        visibility: hidden; /* Hidden by default. Visible on click */
    }

    /* Show the snackbar when clicking on a button (class added with JavaScript) */
    :global(.snackbarshow) {
        visibility: visible;
        min-width: 250px;
        margin-left: -125px; /* Divide value of min-width by 2 */
        background-color: #333;
        color: #fff; 
        text-align: center;
        border-radius: 5px;
        padding: 16px;
        position: fixed;
        z-index: 11;
        left: 50%;
        bottom: 30px;
    }
</style>