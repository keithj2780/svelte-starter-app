<a {href} class={className} {style} on:click|preventDefault={onClick}><slot></slot></a>
      
<script>
    import { onMount, createEventDispatcher } from 'svelte';
    import { push } from 'svelte-spa-router';

    let cssClass = '';
    export let href = '/';
    export let className = '';
    // export let title = '';
    export let style = '';
    
    export { cssClass as class };

    onMount(() => {
        className = className || cssClass;
    });

    const dispatch = createEventDispatcher();
    
    // this will enable `<Link on:click={...} />` calls
    function onClick(e) {
        let fixedHref = href;
    //     // this will rebase anchors to avoid location changes
    //     if (fixedHref.charAt() !== '/') {
    //         fixedHref = window.location.pathname + fixedHref;
    //     }
        push(fixedHref);
    //     dispatch('click', e);
    }
</script>
