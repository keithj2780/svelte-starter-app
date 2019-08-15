<span class="tagbutton-outer" {style}>
	<button class="tagbutton-inner tagbutton-inner-left" style="background-color:{leftbg}; color:{leftfg}" on:click="{(e) => { e.preventDefault(); onclick('left')}}">{lefttext}</button>
	<button class="tagbutton-inner tagbutton-inner-right" style="background-color:{rightbg}; color:{rightfg}" on:click="{(e) => {e.preventDefault(); onclick('right')}}">{righttext}</button>
</span>


<script>
	import { createEventDispatcher } from 'svelte';

    export let righttext="";
	export let lefttext="";
    export let leftbg="";
    export let rightbg="";
    export let leftfg="";
    export let rightfg="";
	export let style = "";

    const dispatch = createEventDispatcher();

    function onclick(side) {
        dispatch('click',side)
    }
</script>

<style>
	.tagbutton-outer {
		background: var(--componentbgcolor);
		height: 30px;
		font-size: var(--componentfontsize);
		display: inline-flex;
		justify-content: space-between;
		align-items: center;
		transform: translateY(-1px);
		margin: 0 5px;
		border-radius: 5px;
		box-shadow: 3px 3px 15px 1px rgba(0,0,0,0.4)
    }
	.tagbutton-outer:hover {
		box-shadow: 3px 3px 15px 1px rgba(0,0,0,0.6)
	}
	.tagbutton-inner {
		height: 30px;
		padding: 0px 7px 1px 7px;
		margin: 0;
		border: none;
		background: none;
		color: var(--componentfgcolor);
		font-weight: bold;
		cursor: pointer;
    }
	.tagbutton-inner-left {
		border-radius: 5px 0px 0px 5px;
	}
	.tagbutton-inner-right {
		border-radius: 0px 5px 5px 0px;
	}
</style>
