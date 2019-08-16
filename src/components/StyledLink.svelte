<a {href} class={className} {style} on:click|preventDefault={onClick}><slot></slot></a>
      
<script>
    //  this is forked from svero package <Link>  Link.svelte
    import { onMount, createEventDispatcher } from 'svelte';
    import { navigateTo } from 'svero';

    let cssClass = '';
    export let href = '/';
    export let className = '';
    export let title = '';
    export let style = '';
    
    export { cssClass as class };

    onMount(() => {
        className = className || cssClass;
    });

    const dispatch = createEventDispatcher();
    
    // this will enable `<Link on:click={...} />` calls
    function onClick(e) {
        let fixedHref = href;
        // this will rebase anchors to avoid location changes
        if (fixedHref.charAt() !== '/') {
            fixedHref = window.location.pathname + fixedHref;
        }
        navigateTo(fixedHref);
        dispatch('click', e);
    }
</script>
