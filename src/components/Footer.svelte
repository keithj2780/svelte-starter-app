<footer class="footer {style}">
  <p>
    <slot></slot>
  </p>
</footer>
  
<script>
    export let style="";
</script>
<style>
    .footer {
        background-color: #aaaaaa;
        padding: 5px;
        color: #444;
        bottom:12px;
        position: fixed;
        bottom: 0;
        width: 100%;
        text-align: center;
        font-size: 14px;
    }
</style>


