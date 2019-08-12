<div class="card-container" {style} on:click={() => flipped = !flipped}>
	<div class="card">
		{#if flipped}
		<div class="side" {sideBStyle} transition:flip>
			<slot name="sideA"></slot>
		</div>
		{:else}
		<div class="side back" {sideBStyle} transition:flip>
            <slot name="sideB"></slot>
        </div>
		{/if}
	</div>
</div>

<script>
	export let flipped = false
    export let style;
    export let sideAStyle;
    export let sideBStyle;
	
	export function flip(node, {
		delay = 0,
		duration = 500
	}) {
		return {
			delay,
			duration,
			css: (t, u) => `
				transform: rotateY(${1 - (u * 180)}deg);
				opacity: ${1 - u};
			`
		};
	}
</script>

<style>
	.card-container {
		position: relative;
		height: 200px;
		width: 400px;
		cursor:pointer;
	}
	
	.card {
		width: 100%;
		height: 100%;
		position: absolute;
		perspective: 600;
	}
	
	.side {
		position: absolute;
		height: 100%;
		width: 100%;
		background-color: orange;
		overflow: hidden;
		color: #fff;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
	.back {
		background-color: grey;
	}
</style>