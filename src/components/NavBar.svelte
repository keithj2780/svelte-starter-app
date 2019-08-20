<script src="https://cdn.jsdelivr.net/npm/feather-icons/dist/feather.min.js">

  /* Toggle between adding and removing the "responsive" class to topnav when the user clicks on the icon */
  export function toggle() {
    var x = document.getElementById("myTopnav");
    if (x.className === "topnav") {
      x.className += " responsive";
    } else {
      x.className = "topnav";
    }
    //console.log("x is "+x.className);
  }

  export function closeDropdown() {
    let items = document.getElementsByClassName("dropdown-content");
    for (let i = 0; i < items.length; i++) {
      //console.log("items[i].style is ");
      //console.log(items[i].style);
      //items[i].style = "display:none";
      //items[i].style.visibility = "hidden";
    }
  }
</script>


<div class="topnav" id="myTopnav">
    <div class="topnav-right icon">
        <a href="javascript:void(0);" on:click={toggle}><i class="fa fa-bars"></i></a>
    </div>
    <div on:click={closeDropdown}>
      <slot></slot>
  </div>
</div>
<style>


/* Add a black background color to the top navigation */
:global(.topnav) {
  background-color: var(--navbackground);
  overflow: hidden;
}

:global(.topnav img) {
		height:16px;
		width:16px;
}

/* Style the links inside the navigation bar */
:global(.topnav a) {
  float: left;
  color: var(--navforeground); 
  text-align: center;
  padding: var(--navpadding);
  text-decoration: none;
  font-size: var(--navfontsize);
}

/* Hide the link that should open and close the topnav on small screens */
.topnav .icon {
  display: none;
}

/* Right-aligned section inside the top navigation */
:global(.topnav-right) {
  float: right;
}

/* Dropdown container - needed to position the dropdown content */
:global(.dropdown) {
  float: left;
  overflow: hidden;
  z-index:1;
}

/* Style the dropdown button to fit inside the topnav */
:global(.dropdown .dropbtn) {
  font-size: var(--navfontsize);
  float:none;
  border: none;
  outline: none;
  color: var(--navforeground);
  padding: var(--navpadding);
  background-color: inherit;
  font-family: inherit;
  margin: 0;
  z-index:1;
  border-radius:0px
}

/* Style the dropdown content (hidden by default) */
:global(.dropdown-content) {
  display: none;
  position: absolute;
  background-color: var(--navbackground);
  min-width: 120px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

:global(.mega-dropdown-content) {
  width:100%;
  left:0;
}

/* Style the links inside the dropdown */
:global(.dropdown-content a) {
  float: none;
  color: var(--navforeground);
  padding: var(--navpadding);
  text-decoration: none;
  display: block;
  text-align: left;
}

/* Add a dark background on topnav links and the dropdown button on hover */
:global(.topnav a:hover, .dropdown:hover .dropbtn) {
  background-color: var(--navbackgroundhover);
  color: white; 
}

/* Add a grey background to dropdown links on hover */
:global(.dropdown-content a:hover) {
  background-color: var(--navbackgroundhover);
  color: var(--navforegroundhover);
  display: block;
}

/* Show the dropdown menu when the user moves the mouse over the dropdown button */
:global(.dropdown:hover .dropdown-content) {
  display: block;
}

/*  make sure icons (eg chevron) don't bloat height */
:global(.dropdown img) {
		height:14px;
}

/* some CSS to support a mega menu */
/* Create three equal columns that floats next to each other */
/* Style the dropdown content (hidden by default) */
:global(.dropdown-content .header ) {
  background-color: rgb(78, 78, 102);
  color:rgb(153, 204, 238);
  padding: 6px;
  margin: 1px;
  text-align:center;
}

:global(.column) {
  float: left;
  width: 33%;
  padding: 0px;
  background-color: var(--navbackground);
}

/* Style links inside the columns */
:global(.column a) {
  float: none;
  color: var(--navforeground);
  padding: var(--navpadding);
  text-decoration: none;
  display: block;
  text-align: left;
}

/* Add a background color on hover */
:global(.column a:hover) {
  background-color: var(--navbackgroundhover);
  color: var(--navforegroundhover);
}

/* Clear floats after the columns */
:global(.row:after) {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - makes the three columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  .column {
    width: 100%;
    height: auto;
  }
}


/* When the screen is less than 600 pixels wide, hide all links, except for the first one ("Home"). Show the link that contains should open and close the topnav (.icon) */
@media screen and (max-width: 600px) {
    :global(.topnav a:not(:first-child), .dropdown .dropbtn) {
    display: none;
  }
  :global(.topnav a.icon) {
    float: right;
    display: block;
  }
}

/* The "responsive" class is added to the topnav with JavaScript when the user clicks on the icon. This class makes the topnav look good on small screens (display the links vertically instead of horizontally) */
@media screen and (max-width: 600px) {
    :global(.topnav.responsive) {position: relative;}
    :global(.topnav.responsive a.icon) {
    position: absolute;
    right: 0;
    top: 0;
  }
  :global(.topnav.responsive a) {
    float: none;
    display: block;
    text-align: left;
  }
  :global(.topnav.responsive .dropdown) {float: none;}
  :global(.topnav.responsive .dropdown-content) {position: relative;}
  :global(.topnav.responsive .dropdown .dropbtn) {
    display: block;
    width: 100%;
    text-align: left;
  }
  :global(.topnav-right) {
    float: none;
  }
}
</style>

