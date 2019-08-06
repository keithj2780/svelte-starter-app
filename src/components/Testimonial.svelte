<div class="testimonial {style}">
    <img src={img} alt={alt} style="width:90px">
    <slot></slot>
</div>

<script>
    export let img;
    export let alt;
    export let style="";

</script>

<style>

/* Style the testimonial with a rounded border, grey background and some padding and margin */
.testimonial {
  border: 2px solid #ccc;
  background-color: var(--componentbgcolor);
  border-radius: 5px;
  padding: 14px;
  margin: 10px 0;
}

/* Clear floats after testimonial */
:global(.testimonial::after) {
  content: "";
  clear: both;
  display: table;
  height:26px;
}

/* Float images inside the testimonial to the left. Add a right margin, and style the image as a circle */
:global(.testimonial img) {
  float: left;
  margin-right: 20px;
  border-radius: 50%;
}

/* Increase the font-size of a span element */
:global(.testimonial span) {
  font-size: 20px;
  margin-right: 15px;
}

/* Add media queries for responsiveness. This will center both the text and the image inside the testimonial */
@media (max-width: 500px) {
    :global(.testimonial) {
    text-align: center;
  }

  :global(.testimonial img) {
    margin: auto;
    float: none;
    display: block;
  }
}
</style>
