
<Container>
        <h1>Employees!</h1>
        <p>We have loads of great Cards full of Employees.</p>
        {#each employees as emp, i}
            {#if i % 2 == 0}
            <div class="row">
                <div class="column">
                    <Card 
                        title={emp.fname+" "+emp.sname} 
                        subtitle={emp.jobtitle} 
                        img={emp.photo} 
                        style=max-width:400px
                        on:contact="{()=>console.log('contact click on '+i)}"
                        on:click="{()=>console.log('click on '+i)}"
                        >
                    Great blurb about employee {i} from {emp.city} who we know as {emp.fname} {emp.sname} 
                    <br /><strong><i class="fa fa-envelope"></i></strong> : {emp.email}
                    <br /><strong>DoB</strong>:{emp.dob.slice(0,10)} 
                    </Card>
                    <br />
                </div>
                <div class="column" style="display:nblockone;min-width:1%;max-width:5%">&nbsp;</div>
                <div class="column">
                    <Card title={employees[i+1].fname+" "+employees[i+1].sname} 
                        subtitle={employees[i+1].jobtitle} 
                        img={employees[i+1].photo} 
                        style=max-width:400px
                        on:contact="{()=>console.log('contact click on '+(i+1))}"
                        on:click="{()=>console.log('click on '+(i+1))}"
                    >
                    Great blurb about employee {i+1} from {employees[i+1].city} who we know as {employees[i+1].fname} {employees[i+1].sname} 
                    <br /><strong><i class="fa fa-envelope"></i></strong> : {employees[i+1].email}
                    <br /><strong>DoB</strong>:{employees[i+1].dob.slice(0,10)} 
                    </Card>
                    <br />
                </div>
            </div>
            {/if}
        {/each}
    </Container>
    
<script>
    import { onMount } from 'svelte';

    import { Card,Container} from '../components/index.js';

    export let employees;

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
