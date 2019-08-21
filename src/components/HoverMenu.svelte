<div class="dropdown">
  <button class="dropbtn" on:mouseenter={()=>dispatch('hover')}>
    {#if isPlace}
    <svg style="width:24px;height:24px" viewBox="0 0 24 24">
      <path fill="#000000" d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" />
    </svg>
    {:else if isInfo}
    <svg style="width:24px;height:24px" viewBox="0 0 24 24">
        <path fill="#000000" d="M11,9H13V7H11M12,20C7.59,20 4,16.41 4,12C4,7.59 7.59,4 12,4C16.41,4 20,7.59 20,12C20,16.41 16.41,20 12,20M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2M11,17H13V11H11V17Z" />
    </svg>
    {:else}
    <svg style="width:24px;height:24px" viewBox="0 0 24 24">
      <path fill="#000000" d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
    </svg>
    {/if}
  </button>
  <div class="dropdown-content">
      {#each items as item}
        {#if item.active}
        <span>
          <a href="javascript:void(0)" on:click={((e) => dispatchCmd(e,item.cmd))}><i class="fa fa-fw {item.icon}"></i>{item.name}
            {#if isTwoLine}
              <div class="line2-content"><i class="fa fa-fw "></i>{item.line2}</div>
            {/if}
          </a>
        </span>
        {/if}
      {/each}
  </div>
</div>

<script>
    import { createEventDispatcher, onMount } from 'svelte';
 
    const dispatch = createEventDispatcher();
    export let items=[];
    export let isPlace=false;
    export let isInfo=false;
    export let isTwoLine=false;

    function dispatchCmd(e,cmd) {
        //console.log(e);
        e.stopPropagation();
        dispatch('menu',cmd);
    }

    export function update(i) {
      items = i;
    }
</script>

<style>
/* Dropdown Button */
.dropbtn {
  background-color: rgb(139, 207, 235,0.3);
  color: white;         
  padding: 4px;
  border: none;
}

/* The container <div> - needed to position the dropdown content */
.dropdown {
  z-index:1;
  position:absolute;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: relative;
  top:0px;
  right:5px;
  background-color: var(--navbackground);
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  font-size: var(--navfontsize);
  z-index: 1;
}

.line2-content {
  font-size: 13px;
  padding: 8px 0 0 0;
  color: #474747;
}
/* Links inside the dropdown */
.dropdown-content a {
  color: black;
  padding: 10px 14px;
  text-decoration: none;
  display: block;
}

/* Change color of dropdown links on hover */
.dropdown-content a:hover {background-color: var(--navbackgroundhover);}

/* Show the dropdown menu on hover */
.dropdown:hover .dropdown-content {display: block;}

/* Change the background color of the dropdown button when the dropdown content is shown */
.dropdown:hover .dropbtn {background-color: rgba(91, 188, 230, 0.5);}
</style>