<div class="callout{hidden} {style}">
        <div class="callout-header">{header}</div>
        <span class="closebtn" on:click={hide1}>×</span>
        <div class="callout-container">
            <slot></slot>
        </div>
    </div>
    
<script>
        //"this.parentElement.style.display='none';"></span>
    export let header="";
    export let hidden="";     //  default to visible
    export let style="";

    export function show() {
        hidden = '';
    }
    export function hide1() {
        console.log('hide');
        hidden = 'Hide';
    }
</script>

<style>
    .calloutHide {
        display:none;
    }

    .callout {
        position: fixed;
        /*  where on the page does it need to be positioned */
        bottom: 35px;
        right: 20px;

        margin-left: 20px;
        max-width: 300px;
        z-index:11;
        border-radius: 14px;
        box-shadow: 0 2px 3px #111, 0 0 0 1px #111;
    }
    
    .callout-header {
        padding: 20px 15px;
        background: #555;
        font-size: 30px;
        color: white;
        border-radius: 14px 14px 0 0;            /* top-left | top-right | bottom-right | bottom-left */
    }
    
    .callout-container {
        padding: 15px;
        background-color: var(--componentbgcolor);
        color: black;
        border-radius: 0 0 14px 14px;        /* top-left | top-right | bottom-right | bottom-left */
    }
    

</style>