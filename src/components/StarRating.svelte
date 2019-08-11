<div class="rating" {style}>
    <input type="radio" name="rating-star" class="rating__control" id="rc1" on:click="{() => value = 1}">
    <input type="radio" name="rating-star" class="rating__control" id="rc2" on:click="{() => value = 2}">
    <input type="radio" name="rating-star" class="rating__control" id="rc3" on:click="{() => value = 3}">
    <input type="radio" name="rating-star" class="rating__control" id="rc4" on:click="{() => value = 4}">
    <input type="radio" name="rating-star" class="rating__control" id="rc5" on:click="{() => value = 5}">
    <label for="rc1" class="rating__item">
        <svg class="rating__star"><use xlink:href="#star"></use></svg>
        <span class="rating__label">1</span>
    </label>
    <label for="rc2" class="rating__item">
        <svg class="rating__star"><use xlink:href="#star"></use></svg>
        <span class="rating__label">2</span>
    </label>
    <label for="rc3" class="rating__item">
        <svg class="rating__star"><use xlink:href="#star"></use></svg>
        <span class="rating__label">3</span>
    </label>
    <label for="rc4" class="rating__item">
        <svg class="rating__star"><use xlink:href="#star"></use></svg>
        <span class="rating__label">4</span>
    </label>
    <label for="rc5" class="rating__item">
        <svg class="rating__star"><use xlink:href="#star"></use></svg>
        <span class="rating__label">5</span>
    </label>	
</div>
<svg xmlns="http://www.w3.org/2000/svg" style="display: none">
    <symbol id="star" viewBox="0 0 26 28">
        <path d="M26 10.109c0 .281-.203.547-.406.75l-5.672 5.531 1.344 7.812c.016.109.016.203.016.313 0 .406-.187.781-.641.781a1.27 1.27 0 0 1-.625-.187L13 21.422l-7.016 3.687c-.203.109-.406.187-.625.187-.453 0-.656-.375-.656-.781 0-.109.016-.203.031-.313l1.344-7.812L.39 10.859c-.187-.203-.391-.469-.391-.75 0-.469.484-.656.875-.719l7.844-1.141 3.516-7.109c.141-.297.406-.641.766-.641s.625.344.766.641l3.516 7.109 7.844 1.141c.375.063.875.25.875.719z"/>
    </symbol>
</svg>

<script>
	import { onMount } from 'svelte';

    export let label="Rating label";
    export let value;
    export let style="";

	onMount(()=>{
        //  set the label depending on the value
        setValue(value);
    });

    export function setValue(r) {
        value = r;
        let elem = document.getElementById("rc"+value);
        if (elem) elem.checked = true;
        else console.log('StarRating didnt find radio with Id rc'+value);
	}

</script>

<style>

.rating {
	--uiRatingSize: var(--ratingSize, 20px);
	--uiRatingColor: var(--ratingColor, #eee);
	--uiRatingColorActive: var(--ratingColorActive, #ffcc00);
	--uiRatingStroke: var(--ratingStroke, #222);
	--uiRatingStrokeWidth: var(--ratingStrokeWidth, 1px);

	display: flex;
    font-size: var(--uiRatingSize);
	color: var(--uiRatingColor);
    position: relative;
}

.rating__control{
	position: absolute;
	left: -9999px;
}

.rating__control:nth-of-type(1):focus ~ .rating__item:nth-of-type(1):before,
.rating__control:nth-of-type(2):focus ~ .rating__item:nth-of-type(2):before,
.rating__control:nth-of-type(3):focus ~ .rating__item:nth-of-type(3):before,
.rating__control:nth-of-type(4):focus ~ .rating__item:nth-of-type(4):before,
.rating__control:nth-of-type(5):focus ~ .rating__item:nth-of-type(5):before {
  content: ""; 
  box-shadow: 0 0 0 4px var(--uiRatingColorActive);
  
  position: absolute;
  top: -.15em;
  right: 0;
  bottom: -.15em;
  left: 0;
  z-index: -1;
}

.rating__item {
	-webkit-tap-highlight-color: transparent;
  cursor: pointer;  
  position: relative;
}

.rating__item {
    padding-left: .25em;
    padding-right: .25em;
}

.rating__star{
	display: block;
	width: 1em;
	height: 1em;

	fill: currentColor;
	stroke: var(--uiRatingStroke);
	stroke-width: var(--uiRatingStrokeWidth);
}

.rating__label{
	position: absolute;
	top: 0;
	left: -9999px;
}

.rating:hover,
.rating__control:nth-of-type(1):checked ~ .rating__item:nth-of-type(1),
.rating__control:nth-of-type(2):checked ~ .rating__item:nth-of-type(-n+2),
.rating__control:nth-of-type(3):checked ~ .rating__item:nth-of-type(-n+3),
.rating__control:nth-of-type(4):checked ~ .rating__item:nth-of-type(-n+4),
.rating__control:nth-of-type(5):checked ~ .rating__item:nth-of-type(-n+5){
	color: var(--uiRatingColorActive);
}

.rating__item:hover ~ .rating__item {
  color: var(--uiRatingColor);
}

.rating {
    --ratingSize: 30px;
    --ratingColor: #eee;
	--ratingColorActive: #ffcc00;
}
</style>
