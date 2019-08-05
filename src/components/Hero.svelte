<div class="hero-image" style=background-image:url({img})>
    <div class="hero-text">
        <slot>
        <h1>H1 Hero Text</h1>
        <p>Para Text</p>
        <button>Button Text</button>
        </slot>
    </div>
</div>

<script>
    export let img;
</script>

<style>

/* The hero image */
.hero-image {
  /* Use "linear-gradient" to add a darken background effect to the image. This will make the text easier to read */
  background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5));

  /* Set a specific height */
  height: 200px;

  /* Position and center the image to scale nicely on all screens */
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
}

/* Place text in the middle of the image */
.hero-text {
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
}
</style>
