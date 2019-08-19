<div class="row" {style}>
    <div class="col-25">
        <label>{label}</label>
    </div>
    <div class="col-75">
        <slot></slot>
    </div>
</div>

<script>
    export let label="";
    export let style="";
</script>

<style>
</style>