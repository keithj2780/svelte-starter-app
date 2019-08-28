<div class="colorpicker" class:hide {style}>
  {#each options as col}
    {#if values.includes(col)}
      <div data-col={col} class=colorpicker-selected style={"background-color:"+col} on:click="{()=>handleClick(col)}"></div>
    {:else}
      <div data-col={col} style={"background-color:"+col} on:click="{()=>handleClick(col)}"></div>
    {/if}
  {/each}
</div>

<script>
    import { createEventDispatcher, onMount } from 'svelte';

    export let style="";
    export let width="";
    export let hide="";
    export let isMulti = false;
    export let values=[];
    export let options = [];

  $: values;

  const dispatch = createEventDispatcher();

  onMount(() => {
    let rows = 2;
    style = "width:"+(7+options.length*52 / rows)+"px; ";
  });

  function handleClick(col) {
    //console.log("handleClick "+values);
    if (isMulti) {
      //let idx = values.findIndex(col);
      if (values.includes(col)) {
        //  deselect it
        values = values.filter((obj)=>{console.log("handleClick "+col+','+obj); return col!==obj});
        //console.log("deselect "+values);
        dispatch('select',values);
      } else {
        //  select it
        values = [...values,col];
        //console.log("select "+values);
        dispatch('select',values);
      }
    } else {    //  it is single select
      values = [col];
      hide=true;
      dispatch('select',values);
    }
  }

  function doClose() {
    this.parentElement.style.display='none';
    dispatch('select',{});
  }

</script>

<style>
.colorpicker {
    background: rgba(255, 255, 255, 0.75);
    padding: 10px;
    border: 1px solid rgba(203, 203, 203, 0.6);
    border-radius: 5px;
    width:200px;
    background-color: var(--componentbgcolor);
    position:absolute;
 }

 .colorpicker:hover {
  box-shadow: 3px 3px 4px rgb(114, 114, 114);
 }

.hide {
    display:none;
}
.colorpicker > div {
    width: 38px;
    display: inline-block;
    height: 38px;
    margin: 5px;
    border-radius: 100%;
    opacity: 0.7;
    border:2px solid var(--componentbgcolor);
}

.colorpicker > div.colorpicker-selected {
  border:2px solid rgb(31, 29, 29);
}

.colorpicker > div:hover {
    opacity: 1;
    box-shadow: 1px 2px 2px rgb(107, 107, 107);
}

</style>