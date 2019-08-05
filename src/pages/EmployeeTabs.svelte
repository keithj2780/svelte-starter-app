<script>
    import Tabs from '../components/Tabs.svelte';
    import Container from '../components/Container.svelte';
    import { onMount } from 'svelte';
    
    export let router = {};
        
        // Those contains useful information about current route status
        router.path; // /test
        router.route; // Route Object
        router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }
    
        export let employees;
        let empId=0;
    
    onMount(() => {
        console.log(employees[0]);
        selectTab('0');     //  this assumes that the first tab's ID is '0'
    });
        
    function openTab(evt) {
        let selectedTabId = evt.target.id;
        selectTab(selectedTabId);
    }
    function selectTab(selectedTabId) {
        //console.log('tabName='+selectedTabId);
        var i, tabcontent, tablinks;

        // Get all elements with class="tabcontent" and hide them (except the selected ID)
        tabcontent = document.getElementsByClassName("tabcontent");
        for (i = 0; i < tabcontent.length; i++) {
            //console.log('tabcontent='+tabcontent[i].id);
            if (tabcontent[i].id === selectedTabId)
                tabcontent[i].style.display = "block";
            else
                tabcontent[i].style.display = "none";
        }

        // Get all elements with class="tablinks" and remove the class "active" (except the selected ID)
        tablinks = document.getElementsByClassName("tablinks");
        for (i = 0; i < tablinks.length; i++) {
            //console.log('tablinks='+tablinks[i].id);
            if (tablinks[i].id === selectedTabId)
                tablinks[i].className = tablinks[i].className += " active";
            else
                tablinks[i].className = tablinks[i].className.replace(" active", "");
        }
    }
    </script>
        
    <style>
        h1 {
            color: grey;
        }
        
    </style>

    <Container>
        <h1>Employee Tabs</h1>
        <p>We have loads of amazing tabs full of Employees.</p> 
        <Tabs id="myTabs">
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
