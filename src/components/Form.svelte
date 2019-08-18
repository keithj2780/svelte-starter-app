<div class="form">
    <div class="container">
        <form class={className} action="">
            <slot></slot>
        </form>
    </div>
</div>

<script>
    export let className;
</script>

<style>
:global(.form input[type=text]), 
:global(.form input[type=password]), 
:global(.form select),
:global(.form textarea) {
  width: 100%;
  padding: 5px;
  border: 1px solid rgb(219, 219, 219);
  border-radius: 4px;
  box-sizing: border-box;
  resize: vertical;
  display:inline-flex;
  background-color:#fff;
}

:global(.form input[type=text]:focus), :global(.form select:focus), :global(.form textarea:focus) {
  border-color: #3273dc;
  box-shadow: 0 0 0 0.125em rgb(50,115,220,0.5);
  outline:0;
}

:global(.form label) {
  padding: 6px 12px 6px 0;
  display: block;
  font-weight:700;
  font-size:16px;
  color:rgb(74,74,74);
  text-align:right;
}

:global(.form button) {
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  float: right;
  margin:16px;
}

/* Style the container */
.container {
  border-radius: 5px;
  background-color: #ffffff;
  padding: 20px;
}

/* Floating column for labels: 25% width */
:global(.col-25) {
  float: left;
  width: 25%;
  margin-top: 6px;
}

/* Floating column for inputs: 75% width */
:global(.col-75) {
  float: left;
  width: 75%;
  margin-top: 6px;
}

/* Clear floats after the columns */
:global(.row:after) {
  content: "";
  display: table;
  clear: both;
}

/* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 600px) {
  :global(.col-25, .col-75, input[type=submit]) {
    width: 100%;
    margin-top: 0;
  }

  :global(.form label) {
    text-align:left;
  }
}
</style>
