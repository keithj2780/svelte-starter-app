{#if tooltip}
<div class="popup tooltip">
        <slot></slot>
        <span class="popuptext {show}" id="myPopup">{popuptext}</span>
</div>
{:else}
<div class="popup" on:click={showPopup}>
    <slot></slot>
    <span class="popuptext {show}" id="myPopup">{popuptext}</span>
</div>
{/if}

<script>
    export let popuptext;
    export let tooltip = false;
    export let ms=5000;
    let show="";

    // When the user clicks on <div>, open the popup
    function showPopup() {
        show = "show";
        //console.log("ms="+ms);

        setTimeout(function(){ show = ""; }, ms);
    }
</script>

<style>
/* Popup container */
:global(.popup) {
  position: relative;
  display: inline-block;
  cursor: pointer;
}

/* The actual popup (appears on top) */
:global(.popup .popuptext) {
  visibility: hidden;
  width: 160px;
  background-color: #555;
  color: #fff;
  text-align: center;
  border-radius: 6px;
  padding: 8px 0;
  position: absolute;
  z-index: 10;
  bottom: 125%;
  left: 50%;
  margin-left: -80px;
}

/* Popup arrow */
:global(.popup .popuptext::after) {
  content: "";
  position: absolute;
  top: 100%;
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: #555 transparent transparent transparent;
}

/* Toggle this class when clicking on the popup container (hide and show the popup) */
:global(.popup .show) {
  visibility: visible;
  -webkit-animation: fadeIn 1s;
  animation: fadeIn 1s;
}

/* Show the tooltip text when you hover over the tooltip container */
:global(.tooltip:hover) .popuptext {
  visibility: visible;
  -webkit-animation: fadeIn 1s;
  animation: fadeIn 1s;
}

/* Add animation (fade in/out the popup) */
@-webkit-keyframes fadeIn {
  from {opacity: 0;} 
  to {opacity: 1;}
}

@keyframes fadeIn {
  from {opacity: 0;}
  to {opacity: 1;}
}

@-webkit-keyframes fadeOut {
  from {opacity: 1;} 
  to {opacity: 0;}
}

@keyframes fadeOut {
  from {opacity: 1;}
  to {opacity: 0;}
}
</style>
