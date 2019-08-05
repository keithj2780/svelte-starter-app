
<div class="tab">
    <slot></slot>
</div>

    

<style>

:root {
    --background: rgb(196, 231, 245);
    --active: rgb(128, 209, 241);
}    
/* Style the tab */
:global(.tab) {
  overflow: hidden;
  border: 0px solid rgb(114, 16, 16);
  background-color: var(--background);
  border-bottom: none;
}

/* Style the buttons that are used to open the tab content */
:global(.tab button) {
  background-color: var(--background);
  float: left;
  outline: none;
  cursor: pointer;
  padding: 14px 16px;
  transition: 0.3s;
  margin: 0px;
  color: rgb(78, 74, 74);
  border: 1px solid var(--background);
  border-radius: 3px;
}

/* Change background color of buttons on hover */
:global(.tab button:hover) {
  background-color: rgb(140, 208, 240);
}

/* Create an active/current tablink class */
:global(.tab button.active) {
  background-color: var(--active);
  border-top: 1px solid rgb(114, 16, 16);
  border-left: 1px solid rgb(114, 16, 16);
  border-right: 1px solid rgb(114, 16, 16);
  border-bottom: 1px solid var(--active);
  border-radius: 1px;
}

/* Style the tab content */
:global(.tabcontent) {
  background-color: var(--componentbgcolor);
  display: none;
  padding: 6px 12px;
  border: 0px solid rgb(98, 99, 96);
  border-top: none;
}
</style>