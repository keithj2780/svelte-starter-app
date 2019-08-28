<Container>
    <h1>Employee Tabs</h1>
    <p>We have loads of amazing tabs full of Employees.</p> 
    <Tabs id="myTabs" bind:this={tabs} >
        <div class="tab">
        {#each employees as emp, i}
            <button class="tablinks" id={i} on:click={openTab}>{emp.fname}</button>
        {/each}
        </div>
        {#each employees as emp, i}
        <div id={i} class="tabcontent">
            <h3>{emp.fname+" "+emp.sname}</h3>
            <p><i class="fa fa-envelope"></i> {emp.email}</p>
            <p>{emp.dob.slice(0,10)}</p>
            <p>{emp.jobtitle}</p>
            <p>{@html emp.bio}</p>
            <p align:centre><img src={emp.photo} alt={emp.fname} style=width:32px;height:32px></p>
            <p>{emp.city}, {emp.state}</p>
        </div>
        {/each}
    </Tabs>
</Container>
    

<script>
    import { onMount } from 'svelte';
    import { Tabs,Container} from '../components/index.js';
    
    export let employees;
    let empId=0;
    let tabs;
    
    onMount(() => {
        //console.log(employees[0]);
        tabs.selectTab('0');     //  this assumes that the first tab's ID is '0'
    });
        
    function openTab(evt) {
        let selectedTabId = evt.target.id;
        tabs.selectTab(selectedTabId);
    }
</script>
    
<style>
    h1 {
        color: grey;
    }
    
</style>

