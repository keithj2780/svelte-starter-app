<div class="snackbar{show} {style}">
    <slot></slot>
</div>

<script>
	import { createEventDispatcher } from 'svelte';

    export let show="";
    export let style="";


	const dispatch = createEventDispatcher();

    export function showToast() {
        let ms = 3000;
        show = "show";
        setTimeout(function(){ show = ""; dispatch('close',{}); }, ms);
    }

    export function showToastForMS(ms) {
        show = "show";
        // After 3 seconds, remove the show class from DIV
        setTimeout(function(){ show=""; dispatch('close',{}); }, ms);
    }

</script>

<style>
    /* The snackbar - position it at the bottom and in the middle of the screen */
    :global(.snackbar) {
        visibility: hidden; /* Hidden by default. Visible on click */
    }

    /* Show the snackbar when clicking on a button (class added with JavaScript) */
    :global(.snackbarshow) {
        visibility: visible; /* Show the snackbar */
        min-width: 250px; /* Set a default minimum width */
        margin-left: -125px; /* Divide value of min-width by 2 */
        background-color: #333; /* Black background color */
        color: #fff; /* White text color */
        text-align: center; /* Centered text */
        border-radius: 2px; /* Rounded borders */
        padding: 16px; /* Padding */
        position: fixed; /* Sit on top of the screen */
        z-index: 11; /* Add a z-index if needed */
        left: 50%; /* Center the snackbar */
        bottom: 30px; /* 30px from the bottom */

        /* Add animation: Take 0.5 seconds to fade in and out the snackbar. 
        However, delay the fade out process for 2.5 seconds */
        -webkit-animation: fadein 0.5s, fadeout 0.5s 2.5s;
        animation: fadein 0.5s, fadeout 0.5s 2.5s;
    }

    /* Animations to fade the snackbar in and out */
    @-webkit-keyframes fadein {
        from {bottom: 0; opacity: 0;} 
        to {bottom: 30px; opacity: 1;}
    }

    @keyframes fadein {
        from {bottom: 0; opacity: 0;}
        to {bottom: 30px; opacity: 1;}
    }

    @-webkit-keyframes fadeout {
        from {bottom: 30px; opacity: 1;} 
        to {bottom: 0; opacity: 0;}
    }

    @keyframes fadeout {
        from {bottom: 30px; opacity: 1;}
        to {bottom: 0; opacity: 0;}
    }
</style>