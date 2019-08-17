<div class="sideCurtain {expand}" {style}>
    <span class="closebtn" on:click={closeCurtain}>&times;</span>
    <slot></slot>
</div>

<script>
  export let style="";
  //export let width="250px";
  export let divToSlide;
  let expand="";

  export function openCurtain() {
    //console.log("openCurtain");
    //document.getElementsByClassName("sideCurtain")[0].style.width = width;
    expand="expand";
    if (divToSlide && document.getElementById(divToSlide))
      document.getElementById(divToSlide).style.marginLeft = width;   //  slide all of body across too
  }
  export function closeCurtain() {
    expand="";
    //document.getElementsByClassName("sideCurtain")[0].style.width = "0";
    if (divToSlide && document.getElementById(divToSlide))
      document.getElementById(divToSlide).style.marginLeft = "0";  //  slide all of body back
  }

</script>
<style>
.sideCurtain {
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: var(--navbackground); 
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px;
  transition: 0.5s;
}

.expand {
  width:250px;
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
    background-color: var(--navbackgroundhover);
    color: var(--navforegroundhover);
}

/* On smaller screens, where height is less than 450px, change the style of the sideCurtain (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sideCurtain {padding-top: 15px;}
  .sideCurtain a {font-size: 18px;}
}
</style>