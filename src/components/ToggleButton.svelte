<span text-align = "center">
    <label class = "switch">
    <input type = "checkbox" bind:checked={checked} >
    <div class="slider round"></div>
</span>

<script>
    export let checked;
</script>

<style>
.switch {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 11px;
  border-radius: 12px;
  border: 2px solid #c8ccd4;
}
 
.switch input {
  display:none;
}
 
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgb(156, 148, 148);
  transition: .4s;
}
 
 
.slider:before {
  position: absolute;
  content: "";
  height: 20px;
  width: 20px;
  left: 1px;
  bottom: 0px;
  background-color: white;
  border: 2px solid #c8ccd4;
  transition: .4s;
}
 
input:checked + .slider {
  background-color: var(--buttonbgcolor);
}
 
input:focus + .slider {
  box-shadow: 0 0 1px var(--buttonbgcoloractive);
}
 
input:checked + .slider:before {
  transform: translateX(25px);
}
 
.slider.round {
  border-radius: 12px;
  border:1px gray;
}
 
.slider.round:before {
  border-radius: 50%;
}

</style>