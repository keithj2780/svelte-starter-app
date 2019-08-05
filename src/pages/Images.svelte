<script>
    import { onMount } from 'svelte';

    import Carousel from '../components/Carousel.svelte';
    import Container from '../components/Container.svelte';
    export let router = {};
        
    var slideIndex = 1;

    onMount(() => {

    });

    let carousel;

</script>
<style>
</style>
<Container>
<Carousel bind:this={carousel}>
        <div class="slideshow-container">
    
                <!-- Full-width images with number and caption text -->
                <div class="mySlides fade">
                    <div class="numbertext">1 / 3</div>
                    <img src="https://picsum.photos/id/100/2500/1656" style="width:100%">
                    <div class="text">Caption Text</div>
                </div>
                
                <div class="mySlides fade">
                    <div class="numbertext">2 / 3</div>
                    <img src="https://picsum.photos/id/1001/5616/3744" style="width:100%">
                    <div class="text">Caption Two</div>
                </div>
                
                <div class="mySlides fade">
                    <div class="numbertext">3 / 3</div>
                    <img src="https://picsum.photos/id/10/2500/1667" style="width:100%">
                    <div class="text">Caption Three</div>
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
            </div>
        

</Carousel>
</Container>