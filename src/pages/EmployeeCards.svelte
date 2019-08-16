
<Container>
        <h1>Employees!</h1>
        <p>We have loads of great Cards full of Employees.</p>
        {#each employees as emp, i}
            {#if i % 2 == 0}
            <div class="row">
                <div class="column">
                    <Card title={emp.name.first+" "+emp.name.last} subtitle={emp.email} img={emp.picture.large} style=width:400px>
                    Great blurb about employee {i} from {emp.location.timezone.description} who we know as {emp.name.first} {emp.name.last} 
                    <br /><strong><i class="fa fa-envelope"></i></strong> : {emp.email}
                    <br /><strong>DoB</strong>:{emp.dob.date.slice(0,10)} 
                    </Card>
                    <br />
                </div>
                <div class="column" style=width:10%>&nbsp;</div>
                <div class="column">
                    <Card title={employees[i+1].name.first+" "+employees[i+1].name.last} subtitle={employees[i+1].email} img={employees[i+1].picture.large} style=width:400px>
                    Great blurb about employee {i+1} from {employees[i+1].location.timezone.description} who we know as {employees[i+1].name.first} {employees[i+1].name.last} 
                    <br /><strong><i class="fa fa-envelope"></i></strong> : {employees[i+1].email}
                    <br /><strong>DoB</strong>:{employees[i+1].dob.date.slice(0,10)} 
                    </Card>
                    <br />
                </div>
            </div>
            {/if}
        {/each}
    </Container>
    
<script>
import { onMount } from 'svelte';
import Card from '../components/Card.svelte';
import Container from '../components/Container.svelte';

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

</script>

<style>
	h1 {
		color: grey;
    }
    
    .column {
        float: left;
        width: 45%;
        background-color: var(--body-color);
    }


</style>
