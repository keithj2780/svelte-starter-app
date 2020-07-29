<script>
    import {Box, Container} from "../components/index.js";

</script>

<style>
	h1 {
		color: grey;
	}
</style>

<Container>

<h1>About this Svelte Component Demo and App Template</h1>


<Box>
    <h3>Svelte is small, fast to run, fast to develop</h3>
    <p>The whole of this app has dependencies on only svelte itself and the svelte-spa-router router.</p>
    <p>Icons (fontawesome et al) and the banner, test data images & carousel images are just about the only things fetched at run time.
        Everything else you see is loaded now.</p>
    <p>This app is approx 110K of JS, CSS, HTML and a few static icons. Consequently it loads very quickly.</p>
    <p>This does <b>nothing</b> except look pretty. Feel free to use it as a template for your app that really does do something, 
        or re-use its' components.
    </p>
</Box>
<br/>
<Box>
    <h3>Where to find stuff</h3>
    <a href="https://svelte.dev">svelte</a> is a fast, tiny non-framework. This app is a demonstrator of that non-framework.
    <p>github source found at <a href="https://github.com/keithj2780/svelte-starter-app">https://github.com/keithj2780/svelte-starter-app</a></p>
    <p>Live Demo at <a href="http://svelte-component-demo.surge.sh/">http://svelte-component-demo.surge.sh/</a></p>
</Box>
</Container>
