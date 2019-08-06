<div class="card" {style}>
    <img src={img} alt={title}>
    <div class="container">
        <h2>{title}</h2>
        <p class="title">{subtitle}</p>
        <slot></slot>
        <p><button class="button"><i class="fa fa-phone"></i> Contact </button></p>
    </div>
</div>

<script>
    export let style;
    export let title;
    export let subtitle;
    export let img;
    
</script>

<style>

/* Add some shadows to create a card effect */
.card {
    padding: 8px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    background-color: var(--componentbgcolor);
    max-width:300px;
}

/* Some left and right padding inside the container */
.card .container {
  padding: 0 16px;
}

/* Clear floats */
.container::after, .row::after {
  content: "";
  clear: both;
  display: table;
}

.card .title {
  color: grey;
}

.card .button {
  border: none;
  outline: 0;
  display: inline-block;
  padding: 8px;
  text-align: center;
  cursor: pointer;
  width: 100%;
}

.card .button:hover {
  background-color: #555;
}

.card img {
    display: block;
    width: 128px;
    height: 128px;
    margin-left: auto;
    margin-right: auto;
}

</style>
