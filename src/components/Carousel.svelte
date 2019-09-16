<div class="carousel" height=400px>
        <slot></slot>
    </div>
    
<script>
    import { onMount } from 'svelte';

    var slideIndex = 1;

    onMount(() => {
        showSlides(slideIndex);        
    });

    export function plusSlides(n) {
        showSlides(slideIndex += n);
    }
    export function currentSlide(n) {
        showSlides(slideIndex = n);
    }

    function showSlides(n) {
        var i;
        var slides = document.getElementsByClassName("mySlides");
        var dots = document.getElementsByClassName("dot");
        if (n > slides.length) {slideIndex = 1} 
        if (n < 1) {slideIndex = slides.length}
        for (i = 0; i < slides.length; i++) {
            slides[i].style.display = "none"; 
        }
        for (i = 0; i < dots.length; i++) {
            dots[i].className = dots[i].className.replace(" active", "");
        }
        slides[slideIndex-1].style.display = "block"; 
        dots[slideIndex-1].className += " active";
    }

</script>
        
<style>

    /* Slideshow container */
    :global(.slideshow-container) {
        max-width: 1000px;
        position: relative;
        margin: auto;
    }

    /* Hide the images by default */
    :global(.carousel .mySlides) {
        display: none;
        object-fit: cover;
    }

    /* Next & previous buttons */
    :global(.carousel .prev) {
        cursor: pointer;
        position: absolute;
        left:0;
        top: 50%;
        width: auto;
        margin-top: -22px;
        padding: 16px;
        color: white;
        font-weight: bold;
        font-size: 18px;
        transition: 0.6s ease;
        border-radius: 0 3px 3px 0;
        user-select: none;
    }

    /* Position the "next button" to the right */
    :global(.carousel .next) {
        cursor: pointer;
        position: absolute;
        right: 0;
        top: 50%;
        width: auto;
        margin-top: -22px;
        padding: 16px;
        color: white;
        font-weight: bold;
        font-size: 18px;
        transition: 0.6s ease;
        user-select: none;
        border-radius: 3px 0 0 3px;
    }

    /* On hover, add a black background color with a little bit see-through */
    :global(.carousel .prev:hover), :global(.carousel .next:hover) {
        background-color: rgba(0,0,0,0.8);
        text-decoration: none;
    }

    /* Caption text */
    :global(.carousel .text) {
        color: #f2f2f2;
        font-size: 15px;
        padding: 8px 12px;
        position: absolute;
        bottom: 8px;
        width: 100%;
        text-align: center;
    }

    /* Number text (1/3 etc) */
    :global(.carousel .numbertext) {
        color: #f2f2f2;
        font-size: 12px;
        padding: 8px 12px;
        position: absolute;
        top: 0;
    }

    /* The dots/bullets/indicators */
    :global(.carousel .dot) {
        cursor: pointer;
        height: 15px;
        width: 15px;
        margin: 0 2px;
        background-color: #bbb;
        border-radius: 50%;
        display: inline-block;
        transition: background-color 0.6s ease;
    }

    :global(.carousel .active) {
        background-color: #4c4d4b;
    }

    :global(.carousel .dot:hover) {
        background-color: #4c4d4b;
    }

    /* Fading animation */
    :global(.carousel .fade) {
        -webkit-animation-name: fade;
        -webkit-animation-duration: 1.5s;
        animation-name: fade;
        animation-duration: 1.5s;
    }

    @-webkit-keyframes fade {
        from {opacity: .4} 
        to {opacity: 1}
    }

    @keyframes fade {
        from {opacity: .4} 
        to {opacity: 1}
    }
</style>
