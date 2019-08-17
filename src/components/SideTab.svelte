<div class="sidenav {side}">
    <slot></slot>
</div>

<script>
  export  let side="left";   //  default to LHS of screen
</script>
  
<style>
/* Style the links inside the sidenav */
:global(.sidenav a) {
  position: fixed; /* Position them relative to the browser window */
  transition: 0.3s; /* Add transition on hover */
  padding: 15px; /* 15px padding */
  width: 80px; /* Set a specific width */
  text-decoration: none; /* Remove underline */
  font-size: 20px; /* Increase font size */
  background-color: var(--navbackground);
  color: var(--textcolor);
  z-index:1;
}

:global(.sidenav.left .sidenavitem ) {
  left: -60px; /* Position them outside of the screen */
  border-radius: 0 5px 5px 0; /* Rounded corners on the top right and bottom right side */
  text-align:right;
}


:global(.sidenav.left .sidenavitem:hover) {
  left: 0; /* On mouse-over, make the elements appear as they should */
}



:global(.sidenav.right .sidenavitem) {
  right: -60px;
  border-radius: 5px 0 0 5px; /* Rounded corners on the top right and bottom right side */
  text-align:left;
}

:global(.sidenav.right .sidenavitem:hover) {
  right: 0; /* On mouse-over, make the elements appear as they should */
}

/* This default should never be used (unless there's only a single tab)... subsequent ones would overwrite */
:global(.sidenav .sidenavitem) {
  top: 20px;
  background-color: var(--navbackground);
}


</style>