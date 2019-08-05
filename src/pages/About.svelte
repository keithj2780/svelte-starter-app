<!-- ./pages/About.svelte -->
<script>
    import Container from '../components/Container.svelte';
    import Section from '../components/Section.svelte';
    import Box from '../components/Box.svelte';
    import Toast from '../components/Toast.svelte';
    import Chip from '../components/Chip.svelte';
    import Badge from '../components/Badge.svelte';

	import Popup from "../components/Popup.svelte";
	import Callout from "../components/Callout.svelte";
    
    export let router = {};
  
    // Those contains useful information about current route status
    router.path;
    router.route
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

    let name = 'Svelte';
    let toast1;
    let toast2;

	let calloutComponent;
	export function doShowCallout() {
		calloutComponent.show();
	}

</script>

<style>
	h1 {
		color: brown;
	}
</style>

<h1>About {name}!</h1>
<p>Route is {router.path}</p>
<p>Path is {router.route}</p>
<p>Params from URL are {JSON.stringify(router.params)} and the keys are specified in the router</p>
<Container>
    <Section>
    <Box>
        <h3>{name} Box Demo for {router.params.who} of {router.params.where}.</h3>
        <p><em>(mouse over for blur effect)</em></p>
        <p>{name} is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, {name} shifts that work into a compile step that happens when you build your app.</p>
        <p>Instead of using techniques like virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes.</p>
    </Box>
    </Section>
    <button on:click="{() => toast1.showToastForMS(700)}" class="badgeContainer"><span>Toast demo</span>
        <span><Badge>700ms</Badge></span>
    </button>
    <button on:click="{() => toast2.showToastForMS(3000)}"  class="badgeContainer">Another Toast demo
            <span><Badge>3s</Badge></span>
    </button>
    <Section>
        <Chip img="https://randomuser.me/api/portraits/thumb/men/44.jpg" alt="Home">Berts Chip</Chip>
        <Chip img="https://randomuser.me/api/portraits/thumb/women/44.jpg" alt="Home">Bettys Chip</Chip>
    </Section>

    <Container>
        <div class="badgeContainer">
        <span><Badge>Recommended</Badge></span>
        <Popup popuptext="Great hovering" tooltip=true>
            <Box>Tooltip Demo happens for 3 secs if you hover over this box</Box>
        </Popup>
        </div>
    </Container>
    <Container>
        <Box class="badgeContainer">
            <Popup popuptext="Thanks for the hover" tooltip=true>
                Tooltip Demo happens for 3 secs if you hover over this text
            </Popup>
        </Box>
    </Container>
    <Container>
        <Popup popuptext="Thanks for the click" ms=3000>Popup Demo happens for 3 secs if you click this text</Popup>
        <Section><button on:click={doShowCallout}>Click to show the callout again</button></Section>
    </Container>

</Container>
<Toast id='toast-1' bind:this={toast1} >This is some toast</Toast>
<Toast id='toast-2' bind:this={toast2} ><Chip img="https://randomuser.me/api/portraits/thumb/men/79.jpg" alt="Home">Chippo</Chip></Toast>
<Callout bind:this={calloutComponent} header="This is a callout">Maybe you should consider a callout when you next need to ask your users if they know about cookies</Callout>

