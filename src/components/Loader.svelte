{#if type==="7"}
  {#if modal}
  <div class="{modalClass} {hidden}" {style}>
      <div class="{hidden} loaderStyle7 centered" {style}>
      </div>
  </div>
  {:else}
  <div class="{hidden} loaderStyle7" {style}>
  </div>
  {/if}
{:else}
  {#if modal}
  <div class="{modalClass} {hidden}" {style}>
      <div class="loaderbase {hidden} loader{speed}s loaderStyle{type} centered" {style}>
      </div>
  </div>
  {:else}
      <div class="loaderbase {hidden} loader{speed}s loaderStyle{type}" {style}>
  </div>
  {/if}
{/if}

<script>
    import {onMount, createEventDispatcher} from 'svelte';

    export let style;
    export let timeout=0;
    export let hidden;
    export let modal;
    export let speed="1";
    export let type="1";
    let modalClass;

	const dispatch = createEventDispatcher();

    onMount(() => {
        hidden="hide";
        modalClass="";
    });
    export function hide() {
        hidden='hide';
        modalClass="";
    }
    export function show() {
        hidden="";
        if (modal) modalClass="overlay";
        else       modalClass="";

        console.log('timeout='+timeout);
        console.log('modalClass='+modalClass);
        if (timeout > 0) 
            setTimeout(function(){ hide(); dispatch('close',{}); }, timeout);
    }
</script>
<style>
.loaderbase {
  display: inline-block;
  border: 8px solid #f3f3f3; /* Light grey */
  border-top: 8px solid #3498db; /* Blue */
  width: 24px;
  height: 24px;
}

.loader1s {
  animation: spin 1s linear infinite;
}

.loader2s {
  animation: reversespin 2s linear infinite;
}

.loader3s {
  animation: spin 3s linear infinite;
}

.loaderStyle1 {
  border-radius: 50%;
}

.loaderStyle2 {
  border-radius: 50%;
  border-top: 12px solid #3498db;
  border-right: 12px solid rgb(62, 72, 94);
  border-bottom: 12px solid #3498db;
  border-left: 12px solid rgb(62, 72, 94);
}

.loaderStyle3 {
  border-radius: 50%;
  border-bottom: 8px solid #3498db;
}

.loaderStyle7,
.loaderStyle7:before,
.loaderStyle7:after {
  display: inline-block;
  border-radius: 50%;
  width: 2.5em;
  height: 2.5em;
  -webkit-animation-fill-mode: both;
  animation-fill-mode: both;
  -webkit-animation: load7 1.8s infinite ease-in-out;
  animation: load7 1.8s infinite ease-in-out;
}
.loaderStyle7 {
  color: #99afdf;
  font-size: 10px;
  position: relative;
  text-indent: -9999em;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-animation-delay: -0.16s;
  animation-delay: -0.16s;
}
.loaderStyle7:before,
.loaderStyle7:after {
  content: '';
  position: absolute;
  top: 0;
}
.loaderStyle7:before {
  left: -3.5em;
  -webkit-animation-delay: -0.32s;
  animation-delay: -0.32s;
}
.loaderStyle7:after {
  left: 3.5em;
}
@-webkit-keyframes load7 {
  0%,
  80%,
  100% {
    box-shadow: 0 2.5em 0 -1.3em;
  }
  40% {
    box-shadow: 0 2.5em 0 0;
  }
}
@keyframes load7 {
  0%,
  80%,
  100% {
    box-shadow: 0 2.5em 0 -1.3em;
  }
  40% {
    box-shadow: 0 2.5em 0 0;
  }
}

.centered {
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%,-50%);
  transform: translate(-50%,-50%);

}
.overlay {
  position: fixed; /* Sit on top of the page content */
  width: 100%; /* Full width (cover the whole page) */
  height: 100%; /* Full height (cover the whole page) */
  top: 0; 
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0,0,0,0.5); /* Black background with opacity */
  z-index: 2; /* Specify a stack order in case you're using a different order for other elements */
  cursor: pointer; /* Add a pointer on hover */
}

.hide {
    display:none;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
@keyframes reversespin {
  0% { transform: rotate(0deg); }
  50% { transform: rotate(-360deg); }
  100% { transform: rotate(0deg); }
}
</style>
