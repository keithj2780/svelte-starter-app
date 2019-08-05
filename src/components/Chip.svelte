<div class="chip">
    <img src={img} alt={alt} width="96" height="96">
    <slot></slot>
</div>

<script>
    export let img;
    export let alt;
</script>

<style>
.chip {
  display: inline-block;
  padding: 0 25px;
  height: 50px;
  font-size: 16px;
  line-height: 50px;
  border-radius: 25px;
  background-color: var(--navbackground);
  border: 1px solid rgb(102, 102, 102);
}

.chip:hover {
    box-shadow: 0 2px 2px rgb(139, 150, 250)
}

.chip img {
  float: left;
  margin: 0 10px 0 -25px;
  height: 50px;
  width: 50px;
  border-radius: 50%;
}
</style>