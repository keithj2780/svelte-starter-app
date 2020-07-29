<Container>
<Carousel bind:this={carousel}>
        <div class="slideshow-container">
    
                <!-- Full-width images with number and caption text -->
                <div class="mySlides fade">
                    <div class="numbertext">1 / {max}</div>
                    <img src="https://picsum.photos/id/100/2500/1656" style="width:100%" alt="Beach">
                    <div class="text">Caption Text</div>
                </div>
                
                <div class="mySlides fade">
                    <div class="numbertext">2 / {max}</div>
                    <img src="https://picsum.photos/id/1001/5616/3744" style="width:100%" alt="Beach2">
                    <div class="text">Caption Two</div>
                </div>
                
                <div class="mySlides fade">
                    <div class="numbertext">3 / {max}</div>
                    <img src="https://picsum.photos/id/10/2500/1667" style="width:100%" alt="Sea">
                    <div class="text">Caption Three</div>
                </div>

                <div class="mySlides fade">
                        <div class="numbertext">4 / {max}</div>
                        <img src="img/world.svg" style="width:100%" alt="World">
                        <div class="text">SVG World</div>
                    </div>

                
                <!-- Next and previous buttons -->
                <a class="prev" on:click="{() => carousel.plusSlides(-1)}">&#10094;</a>
                <a class="next" on:click="{() => carousel.plusSlides(+1)}">&#10095;</a>
            </div>
            <br>
                
            <!-- The dots/circles -->
            <div style="text-align:center">
                <span class="dot active" on:click="{() => carousel.currentSlide(1)}"></span> 
                <span class="dot" on:click="{() => carousel.currentSlide(2)}"></span> 
                <span class="dot" on:click="{() => carousel.currentSlide(3)}"></span> 
                <span class="dot" on:click="{() => carousel.currentSlide(4)}"></span> 
            </div>
        

</Carousel>
</Container>

<script>
    import { onMount } from 'svelte';

    import {Carousel, Container} from '../components/index.js';
    
    var slideIndex = 1;

    onMount(() => {

    });

    let carousel;
    let max = 4;
    
</script>
<style>
:global(svg:hover) {
  fill: red;
}

:global(.mapsvg-region:hover) {
    fill: gray;
}
:global(#GB:hover) {
  fill: blue;
}
</style>