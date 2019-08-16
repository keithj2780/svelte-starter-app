<Container>
    <h1>Employee Tabs</h1>
    <p>We have loads of amazing tabs full of Employees.</p> 
    <Tabs id="myTabs" bind:this={tabs} >
        <div class="tab">
        {#each employees as emp, i}
            <button class="tablinks" id={i} on:click={openTab}>{emp.name.first}</button>
        {/each}
        </div>
        {#each employees as emp, i}
        <div id={i} class="tabcontent">
            <h3>{emp.name.first+" "+emp.name.last}</h3>
            <p>London is the capital city of England.</p>
            <p><i class="fa fa-envelope"></i> {emp.email}</p>
            <p>{emp.dob.date.slice(0,10)}</p>
            <p align:centre><img src={emp.picture.thumbnail} alt={emp.name.first} style=width:32px;height:32px></p>
            <p>{emp.location.timezone.description}</p>
        </div>
        {/each}
    </Tabs>
</Container>
    

<script>
    import Tabs from '../components/Tabs.svelte';
    import Container from '../components/Container.svelte';
    import { onMount } from 'svelte';
    
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

