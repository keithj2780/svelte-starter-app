<div class="sidemenu {side}" style="top:{top}">
	<div class="sidemenutrigger {side}">
		{#if side === 'left'}
		<span class="header {side}">{header}</span>
		<span><svg style="width:24px;height:24px" viewBox="0 0 24 24">
      <path fill="#000000" d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
		</svg>
		</span>
		{:else}
		<span><svg style="width:24px;height:24px" viewBox="0 0 24 24">
      <path fill="#000000" d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
		</svg>
		</span>
		<span class="header {side}">{header}</span>
		{/if}
	</div>
	<slot></slot>
</div>

<script>
  export  let side="left";   	//  default to LHS of screen
	export	let header="Menu";
	export	let top="10px";
</script>

<style>
.header.left {
	float:left;
}

.header.right {
	float:right;
}

.sidemenu {
  position: fixed;
  transition: 0.4s; /* Add transition on hover */
  padding: 2px; 
  width: 100px; 
  text-decoration: none;
  font-size: 20px; 
	top:50px;
  z-index:1;
	float:right;	
}

.sidemenu.left {
  left: -104px;
}

.sidemenutrigger {
  color: black;
	background-color:rgb(131, 132, 157,0.5);
  padding: 16px; 
	min-width:130px;
}
	
.sidemenutrigger.left {
  border-radius: 0 7px 7px 0;
  text-align:right;
}	

:global(.sidemenuitem:hover) {
	background-color:rgb(131, 132, 157,0.2);
	text-decoration:none;
}

.sidemenu.left:hover {
  position: fixed;
  left: 0px; 
}

:global(.sidemenuitem) {
	width:93px;
	margin:0 0 0 0;
  text-align:center;
}
	
:global(.left .sidemenuitem) {
  border-radius: 0 15px 15px 0;
	padding:17px 0 17px 17px;
  float: left;
}

/*		handles RHS menu */
.sidemenu.right {
  right: -104px;
	float:left;	
}

.sidemenutrigger.right {
  border-radius: 7px 0 0 7px;
  text-align:left;
	position:relative;
	left:-104;
	transform: translate(-60px, 0px);
}

.sidemenu.right:hover {
  position: fixed;
  right: 0px; 
}
	
:global(.right .sidemenuitem) {
  border-radius: 15px 0 0 15px;
	padding:17px 17px 17px 0;
  float: left;
}

</style>