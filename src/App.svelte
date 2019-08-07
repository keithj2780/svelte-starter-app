<script>
	import { onMount } from 'svelte';
	import { Link, navigateTo } from 'svero';

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
	<Link href="/" ><img src="./img/home.svg" alt="Home" /></Link>
	<Link on:click={doOpenCurtain}>Side Curtain</Link>
	<div class="dropdown">
		<button class="dropbtn">Dropdown <i class="fa fa-angle-down"></i></button>
		<div class="dropdown-content" on:click={closeDropdown}>
			<Link href="/cards"><i class="fa fa-fw "></i> Card Demo</Link>
			<Link href="/contact/Berty/Worcester"><i class="fa fa-fw fa-sign-in"></i> Form Demo</Link>
			<Link href="/login"><i class="fa fa-fw "></i> Modal Demo</Link>
			<Link href="/table"><i class="fa fa-fw fa-table"></i> Table Demo</Link>
			<Link href="/tabs"><img src="./img/credit-card.svg" alt="Tabs"/> Tabs Demo</Link>
			<Link href="/testimonials"><i class="fa fa-fw fa-user-tie"></i> Testimonials Demo</Link>
			<Link href="/timeline"><i class="fa fa-fw fa-user"></i> Timeline Demo</Link>
		</div>
	</div> 
	<Link href="/carousel">Carousel</Link>
	<div class="dropdown">
		<button class="dropbtn">Mega <i class="fa fa-angle-down"></i></button>
		<div class="dropdown-content mega-dropdown-content" on:click={closeDropdown}>
			<div class="header">
				<h2>Mega Menu</h2>
			</div> 
			<div class="row">
				<div class="column">
					<h3>CEOs</h3>
					<Link href="/contact/Elon/Musk/4"><i class="fa fa-fw fa-sign-in"></i> Elon</Link>
					<Link href="/contact/Bill/Gates/3"><i class="fa fa-fw fa-sign-out"></i> Bill G</Link>
					<Link href="/contact/Bill/Clinton/2"><i class="fa fa-fw fa-sign-out"></i> Bill C</Link>
				</div>
				<div class="column">
					<h3>Hikers</h3>
					<Link href="/contact/Arthur/Dent/1"><i class="fa fa-fw fa-share"></i> Arthur</Link>
					<Link href="/contact/Dirk/Gently/5"><i class="fa fa-fw fa-circle"></i> Dirk Gently</Link>
					<Link href="/contact/Zaphod/Beeblebrox/4"><i class="fa fa-fw fa-share"></i> Zaphod</Link>
					<Link href="/contact/Ford/Prefect/6"><i class="fa fa-fw fa-circle"></i> Ford Prefect</Link>
				</div>
				<div class="column">
					<h3>Seinfeld</h3>
					<Link href="/contact/Cosmo/Kramer/5"><i class="fa fa-fw fa-square"></i> Cosmo</Link>
					<Link href="/contact/Jerry/Seinfeld/4"><i class="fa fa-fw fa-square"></i> Jerry</Link>
					<Link href="/contact/George//1"><i class="fa fa-fw fa-square"></i> George</Link>
					<Link href="/contact/Elaine/Benice/2"><i class="fa fa-fw fa-forward"></i> Elaine</Link>
				</div>
			</div>
		</div>
	</div>
	<Link href="/contact">Contact</Link>
	<div class="topnav-right">
		<Link href="/about/Dorothy/Kansas">Misc</Link>
		<Link href="/login"><i class="fa fa-sign-in"></i></Link>
	</div>
</NavBar>

<div class="body">

<Hero img="./img/stars.jpg">
	<h1>Svelte Component Demo and App Template</h1>
	<p>The compact, ultra fast non-framework!</p>
</Hero>

<SideCurtain bind:this={sideSlider}>
	<Link href="/about" on:click={doCloseCurtain}>Misc</Link>
	<Link href="/contact" on:click={doCloseCurtain}>Contact</Link>
	<Container>
		<Chip img="https://randomuser.me/api/portraits/thumb/men/51.jpg" alt="Random Dude"> Chippy</Chip>
		<p>Quick paragraph about svelte</p>
	</Container>
</SideCurtain>
<Routes/>
</div>

<Footer>
	<Link href="/">Home</Link> | 
	<Link href="/about/Bill/New%20York">Misc</Link> | 
	<Link href="/login">Login</Link> | 
	<Link href="/table">Table</Link> | 
	<Link href="/tabs">Tabs</Link> | 
	<Link href="/contact/Edward/Scissorhands">Contact</Link> | 
	<Link href="/cards">Cards</Link> | 
	<Link href="/testimonials">Testimonials</Link>
	<p>Copyright © 2019. All Rights Reserved.</p>
</Footer>
</div>