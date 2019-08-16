<div class="sidenav">
    <slot></slot>
</div>
  
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
  text-align:right;
}

</style>