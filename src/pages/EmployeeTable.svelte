<Container>
    <h1>Employee Table</h1>
    <p>We have loads of great rows full of ace Employees.</p>
    <Table>
        <tr class="header">
            <th style="width:5%;">Row</th>
            <th style="width:20%;">Name</th>
            <th style="width:20%;">Email</th>
            <th style="width:15%;">DoB</th>
            <th style="width:10%;">Thumbnail</th>
            <th style="width:20%;">TZ</th>
        </tr>
        {#each employees as emp, i}
        <tr on:click="{()=>handleClick(i)}">
                <td>{i+1}</td>
                <td>{emp.name.first+" "+emp.name.last}</td>
                <td><i class="fa fa-envelope"></i> {emp.email}</td>
                <td>{emp.dob.date.slice(0,10)}</td>
                <td align:center><img src={emp.picture.thumbnail} alt={emp.name.first} style=width:32px;height:32px></td>
                <td>{emp.location.timezone.description}</td>
        </tr>
        {/each}
    </Table>
</Container>
    
<script>
    import { onMount } from 'svelte';
    import { Table,Container} from '../components/index.js';
    
    export let router = {};
        
        // Those contains useful information about current route status
        router.path; // /test
        router.route; // Route Object
        router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }
    
        export let employees;
        let empId=0;
    
    onMount(() => {
        //for (let i=0;i<employees.length;i++) employees[i].id = i;
        //console.log(employees[0]);
    });
    function handleClick(e) {
        console.log('got click on row '+e);
    }
</script>
    
<style>
    h1 {
        color: grey;
    }
    
</style>

