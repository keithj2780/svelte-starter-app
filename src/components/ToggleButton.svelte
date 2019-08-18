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
  height: 14px;
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
  background-color: #333333;
  transition: .4s;
}
 
 
.slider:before {
  position: absolute;
  content: "";
  height: 20px;
  width: 20px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  transition: .4s;
}
 
input:checked + .slider {
  background-color: #00FF00;
}
 
input:focus + .slider {
  box-shadow: 0 0 1px #00FF00;
}
 
input:checked + .slider:before {
  transform: translateX(24px);
}
 
.slider.round {
  border-radius: 34px;
}
 
.slider.round:before {
  border-radius: 50%;
}

</style>