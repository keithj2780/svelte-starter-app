<div class="sidenav">
    <slot></slot>
</div>
  
<script>
    import { Link, navigateTo } from 'svero';
    import { onMount, tick } from 'svelte';
    export let top;
    export let background;

    onMount(async () => {

        setTimeout(function() {
            var n=40;   //  px spacing between each tab
            var elems = document.getElementsByClassName("sidenavitem");
            console.log(elems);
            for (var i = 0; i < elems.length; i++) {
                elems[i].style.top = ""+n+'px';
                elems[i].style.textAlign = "right";
                //elems[i].style.backgroundColor = background;
                //console.log(elems[i]);
                n+=60;
            }
        },1);
        await tick();
    });
</script>

<style>
/* Style the links inside the sidenav */
:global(.sidenav a) {
  position: fixed; /* Position them relative to the browser window */
  left: -60px; /* Position them outside of the screen */
  transition: 0.3s; /* Add transition on hover */
  padding: 15px; /* 15px padding */
  width: 80px; /* Set a specific width */
  text-decoration: none; /* Remove underline */
  font-size: 20px; /* Increase font size */
  background-color: var(--navbackground);
  color: var(--textcolor);
  border-radius: 0 5px 5px 0; /* Rounded corners on the top right and bottom right side */
  z-index:1;
}

:global(.sidenav) {
  left: 0; /* default */
}

:global(.sidenav a:hover) {
  left: 0; /* On mouse-over, make the elements appear as they should */
}

/* The about link: 20px from the top with a green background */
:global(.sidenav .sidenavitem) {
  top: 20px;
  background-color: var(--navbackground);
}

</style>