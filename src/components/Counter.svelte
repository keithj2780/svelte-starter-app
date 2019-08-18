<span class="counter-outer" {style}>
	<button on:click="{(e) => { e.preventDefault(); count = count - 1}}">-</button>
	<span class="counter-inner">{count}</span>
	<button on:click="{(e) => {e.preventDefault(); count = count + 1}}">+</button>
</span>


<script>
	export let count = 0;
	export let style = "";
</script>

<style>
	.counter-outer {
		background: white;	/*var(--componentbgcolor);*/
		height: 20px;
		font-size: var(--componentfontsize);
		display: inline-flex;
		justify-content: space-between;
		align-items: center;
		transform: translateY(-1px);
		margin: 0 5px;
		border-radius: 3px;
		border: 5px red;
		width: 65px;
		box-shadow: 0 3px 15px 1px rgba(0,0,0,0.3)
	}
	.counter-inner {
		margin: 0 0px;
	}
	button {
		height: 20px;
		padding: 0px 7px 1px 7px;
		margin: 0;
		border: none;
		background: none;
		color: var(--componentfgcolor);
		font-weight: bold;
		cursor: pointer;
	}
</style>
