<div class="callout{hidden} {location}" {style} on:click={(e)=> {e.stopPropagation()}}>
    {#if header}
        <div class="callout-header">{header}</div>
        <span class="closebtn" on:click={(e)=> {e.stopPropagation();hide()}}>
            <svg style="width:24px;height:24px" viewBox="0 0 24 24">
                <path fill="#000000" d="M12,2C17.53,2 22,6.47 22,12C22,17.53 17.53,22 12,22C6.47,22 2,17.53 2,12C2,6.47 6.47,2 12,2M15.59,7L12,10.59L8.41,7L7,8.41L10.59,12L7,15.59L8.41,17L12,13.41L15.59,17L17,15.59L13.41,12L17,8.41L15.59,7Z" />
            </svg>
        </span>
        <div class="callout-container">
            <slot></slot>
        </div>
    {:else}
        <div class="callout-container-no-header">
            <slot></slot>
        </div>
    {/if}
</div>
    
<script>

    import { createEventDispatcher } from 'svelte';

    export let header="";
    export let hidden="";     //  default to visible
    export let style="";
    export let location = "bottom-right";

    const dispatch = createEventDispatcher();

    export function show() {
        hidden = '';
    }
    export function hide() {
        //console.log('hide');
        hidden = 'Hide';
        dispatch('close',{});
    }
</script>
    
<style>

    .calloutHide {
        display:none;
    }
    
    .variableLocation {
        top:    var(--varTop);
        bottom: var(--varBottom);
        left:   var(--varLeft);
        right:  var(--varRight);
    }
    
    .bottom-right {
        bottom: 37px;
        right: 20px;
    }
    
    .top-right {
        top: 5px;
        right: 20px;
    }
    
    .bottom-left {
        bottom: 37px;
        left: 5px;
    }
    
    .top-left {
        top: 5px;
        left: 5px;
    }
    
    .callout {
        position: fixed;
        margin-left: 20px;
        max-width: 300px;
        z-index:5501;
        box-shadow: 0 2px 3px #111, 0 0 0 1px #111;
        border-radius: 14px 14px 14px 14px;            /* top-left | top-right | bottom-right | bottom-left */
    }
    
    .callout-header {
        padding: 20px 15px;
        background: #555;
        font-size: 22px;
        color: white;
        opacity:0.6;
        border-radius: 14px 14px 0 0;            /* top-left | top-right | bottom-right | bottom-left */
    }
    
    .callout-container {
        padding: 15px;
        background-color: rgba(176, 213, 243, 0.5);
        color: var(--textcolor);
        border-radius: 0 0 14px 14px;        /* top-left | top-right | bottom-right | bottom-left */
    }
    
    .callout-container-no-header {
        padding: 15px;
        background-color: rgba(176, 213, 243, 0.5);
        color: var(--textcolor);
        border-radius: 14px 14px 14px 14px;
    }
    
    .closebtn {
        position: absolute;
        top: -20px;
        right: -10px;
        color: white;
        font-size: 30px;
        cursor: pointer;
    }
    
    .closebtn:hover {
        color: lightgrey;
    }
    
    
    </style>