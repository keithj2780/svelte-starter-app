<div class="sideCurtain" {style} id="theSideCurtain">
    <span class="closebtn" on:click={closeCurtain}>&times;</span>
    <slot></slot>
</div>

<script>
  export let style="";

  export function openCurtain() {
    console.log("openCurtain");
    document.getElementById("theSideCurtain").style.width = "250px";
    document.getElementById("main").style.marginLeft = "250px";   //  slide all of body across too (delete this line to prevent that behavior)
  }
  export function closeCurtain() {
    document.getElementById("theSideCurtain").style.width = "0";
    document.getElementById("main").style.marginLeft = "0";  //  slide all of body back (delete this line to prevent that behavior)
  }

</script>
<style>
.sideCurtain {
  height: 100%; /* 100% Full-height */
  width: 0; /* 0 width - change this with JavaScript */
  position: fixed; /* Stay in place */
  z-index: 1; /* Stay on top */
  top: 0;
  left: 0;
  background-color: var(--navbackground); 
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /* 0.5 second transition effect to slide in the sideCurtain */
}

/* The navigation menu links */
:global(.sideCurtain a) {
  padding: 8px 8px 8px 32px;
  text-decoration: none;
  font-size: var(--navfontsize);
  color:var(--navforeground); 
  display: block;
  transition: 0.3s;
}

/* When you mouse over the navigation links, change their color */
:global(.sideCurtain a:hover) {
    background-color: #ddd;
    color: black;
}

/* Style page content - use this if you want to push the page content to the right when you open the side navigation */
:global(#main) {
  transition: margin-left .5s;
}

/* On smaller screens, where height is less than 450px, change the style of the sideCurtain (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sideCurtain {padding-top: 15px;}
  .sideCurtain a {font-size: 18px;}
}
</style>