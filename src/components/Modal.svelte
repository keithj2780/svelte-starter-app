<script>
    import { onMount } from 'svelte';

    // Get the modal
    var modal = document.getElementById('id01');
    
    // When the user clicks anywhere outside of the modal, close it
    window.onclick = function(event) {
        if (event.target == modal) {
        modal.style.display = "none";
        }
    }
    onMount(() => {
        //  swoosh it in
        document.getElementById('id01').style.display='block';
        console.log('swooshed');
    });
</script>

<div id="id01" class="modal">
    <span onclick="document.getElementById('id01').style.display='none'" class="closebtn" title="Close Modal">&times;</span>
    <slot></slot>
</div>

<style>
    /* The Modal (background) */
    :global(.modal) {
        display: none; /* Hidden by default */
        position: fixed; /* Stay in place */
        z-index: 1; /* Sit on top */
        left: 0;
        top: 0;
        width: 100%; /* Full width */
        height: 100%; /* Full height */
        overflow: auto; /* Enable scroll if needed */
        background-color: rgb(0,0,0); /* Fallback color */
        background-color: rgba(0,0,0,0.7); /* Black w/ opacity */
        padding-top: 60px;
    }

    /* Modal Content/Box */
    :global(.modal-content) {
        background-color: #fefefe;
        margin: 5px auto; /* 15% from the top and centered */
        border: 1px solid #888;
        width: 80%; /* Could be more or less, depending on screen size */
    }

    /* Add Zoom Animation */
    :global(.animate) {
        -webkit-animation: animatezoom 0.6s;
        animation: animatezoom 0.6s
    }

    @-webkit-keyframes animatezoom {
        from {-webkit-transform: scale(0)} 
        to {-webkit-transform: scale(1)}
    }

    @keyframes animatezoom {
        from {transform: scale(0)} 
        to {transform: scale(1)}
    }
</style>