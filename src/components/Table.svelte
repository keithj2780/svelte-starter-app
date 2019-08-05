
<table class="table">
    <slot></slot>
</table>

<style>
  table.table {
    border-collapse: collapse; /* Collapse borders */
    width: 100%; /* Full-width */
    border: 1px solid rgb(51, 48, 48); /* Add a grey border */
    font-size: 14px;
    overflow-x:auto;    /* responsive */
    background-color: #a8c5d8;
  }
  
  :global(th) {
    text-align: center;
    padding: 12px;
    border-bottom: 1px solid rgb(124, 122, 122);
  }
  
  :global(td) {
    text-align: left;
    padding: 4px;
    border-bottom: 1px solid rgb(124, 122, 122); 
  }
  
  :global(tr) {
    border-bottom: 1px solid #ddd; 
  }
  
  :global(tr:nth-child(even)) {
    background-color: #98aeb4
  }

  :global(tr.header), :global(tr:hover) {
    /* Add a grey background color to the table header and on hover */
    background-color: #708d94;
  }

</style>