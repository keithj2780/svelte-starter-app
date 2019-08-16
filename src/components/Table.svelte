
<table class="table" {style}>
    <slot></slot>
</table>

<script>
    export let style="";
</script>

<style>
  table.table {
    border-collapse: collapse;
    width: 100%;
    border: 1px solid rgb(51, 48, 48);
    font-size: 14px;
    overflow-x:auto;
    background-color: #a8c5d8;
  }

  :global(.table th) {
    text-align: center;
    padding: 12px;
    border-bottom: 1px solid rgb(124, 122, 122);
  }
  
  :global(.table td) {
    text-align: left;
    padding: 1px;
    border-bottom: 2px solid rgb(124, 122, 122); 
  }
  
  :global(.table tr) {
    border-bottom: 1px solid #ddd; 
  }
  
  :global(.table tr:nth-child(even)) {
    background-color: #98aeb4
  }

  :global(.table tr.header) {
    /* Add a grey background color to the table header and on hover */
    background-color: #485a5f;
  }

  :global(.table tr:hover) {
    /* Add a grey background color to the table header and on hover */
    background-color: #bcd7ee;
  }

</style>
