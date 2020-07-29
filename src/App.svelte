<script>
	import { onMount } from 'svelte';
	// import { Link, navigateTo } from 'svero';

	import Routes from './Routes.svelte';
	import NavBar from './components/NavBar.svelte';
	import Hero from './components/Hero.svelte';
	import Container from './components/Container.svelte';
	import Section from './components/Section.svelte';
	import Footer from './components/Footer.svelte';
	import Chip from './components/Chip.svelte';
	import SideCurtain from "./components/SideCurtain.svelte";

	let navbar;
	let sideSlider;

	export function doOpenCurtain() {
		sideSlider.openCurtain();
	}
	export function doCloseCurtain() {
		sideSlider.closeCurtain();
	}
	export function closeDropdown() {
		navbar.closeDropdown();
  	}

	onMount(()=>{
	});

</script>
<style>

</style>
<div id="main">

<NavBar bind:this={navbar}>
	<a href="#/" ><img src="./img/home.svg" alt="Home" /></a>
	<a on:click={doOpenCurtain}>Side Curtain</a>
	<div class="dropdown">
		<button class="dropbtn">Dropdown <i class="fa fa-angle-down"></i></button>
		<div class="dropdown-content" on:click={closeDropdown}>
			<a href="#/cards"><i class="fa fa-fw "></i> Card Demo</a>
			<a href="#/contact/Berty/Worcester"><i class="fa fa-fw fa-sign-in"></i> Form Demo</a>
			<a href="#/login"><i class="fa fa-fw "></i> Modal Demo</a>
			<a href="#/table"><i class="fa fa-fw fa-table"></i> Table Demo</a>
			<a href="#/tabs"><img src="./img/credit-card.svg" alt="Tabs"/> Tabs Demo</a>
			<a href="#/testimonials"><i class="fa fa-fw fa-user-tie"></i> Testimonials Demo</a>
			<a href="#/timeline"><i class="fa fa-fw fa-user"></i> Timeline Demo</a>
		</div>
	</div> 
	<a href="#/carousel">Carousel</a>
	<div class="dropdown">
		<button class="dropbtn">Mega <i class="fa fa-angle-down"></i></button>
		<div class="dropdown-content mega-dropdown-content" on:click={closeDropdown}>
			<div class="header">
				<h2>Mega Menu</h2>
			</div> 
			<div class="row">
				<div class="column">
					<h3>CEOs</h3>
					<a href="#/contact/Elon/Musk/4"><i class="fa fa-fw fa-sign-in"></i> Elon</a>
					<a href="#/contact/Bill/Gates/3"><i class="fa fa-fw fa-sign-out"></i> Bill G</a>
					<a href="#/contact/Bill/Clinton/2"><i class="fa fa-fw fa-sign-out"></i> Bill C</a>
				</div>
				<div class="column">
					<h3>Hikers</h3>
					<a href="#/contact/Arthur/Dent/1"><i class="fa fa-fw fa-share"></i> Arthur</a>
					<a href="#/contact/Dirk/Gently/5"><i class="fa fa-fw fa-circle"></i> Dirk Gently</a>
					<a href="#/contact/Zaphod/Beeblebrox/4"><i class="fa fa-fw fa-share"></i> Zaphod</a>
					<a href="#/contact/Ford/Prefect/6"><i class="fa fa-fw fa-circle"></i> Ford Prefect</a>
				</div>
				<div class="column">
					<h3>Seinfeld</h3>
					<a href="#/contact/Cosmo/Kramer/5"><i class="fa fa-fw fa-square"></i> Cosmo</a>
					<a href="#/contact/Jerry/Seinfeld/4"><i class="fa fa-fw fa-square"></i> Jerry</a>
					<a href="#/contact/George/Costanza/1"><i class="fa fa-fw fa-square"></i> George</a>
					<a href="#/contact/Elaine/Benes/2"><i class="fa fa-fw fa-forward"></i> Elaine</a>
				</div>
			</div>
		</div>
	</div>
	<a href="#/contact">Contact</a>
	<div class="topnav-right">
		<a href="#/about">Miscellaneous Controls</a>
		<a href="#/login"><i class="fa fa-sign-in"></i></a>
	</div>
</NavBar>

<div class="body">

<Hero img="./img/stars.jpg">
	<h1>Svelte Component Demo and App Template</h1>
	<p>The compact, ultra fast non-framework!</p>
</Hero>

<SideCurtain bind:this={sideSlider} divToSlide="main">
	<a href="#/about/Dorothy/Kansas" on:click={doCloseCurtain}>Misc</a>
	<a href="#/contact" on:click={doCloseCurtain}>Contact</a>
	<Container>
		<Chip img="https://randomuser.me/api/portraits/thumb/men/51.jpg" alt="Random Dude"> Chippy</Chip>
		<p>Quick paragraph about svelte</p>
	</Container>
</SideCurtain>
<Routes/>
</div>

<Footer>
	<a href="#/">Home</a> | 
	<a href="#/about/Bill/New%20York">Misc</a> | 
	<a href="#/login">Login</a> | 
	<a href="#/table">Table</a> | 
	<a href="#/tabs">Tabs</a> | 
	<a href="#/contact/Edward/Scissorhands">Contact</a> | 
	<a href="#/cards">Cards</a> | 
	<a href="#/testimonials">Testimonials</a>
	<p>Copyright © 2019. All Rights Reserved.</p>
</Footer>
</div>