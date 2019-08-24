
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


    <SideMenu side="right" header="More" top="100px">
        <a class="sidemenuitem" href="/testimonials">Testimonials</a>
        <a class="sidemenuitem" href="/cards">
			<svg style="width:44px;height:44px" viewBox="0 0 24 24">
        	<path fill="#000000" d="M11,9H13V7H11M12,20C7.59,20 4,16.41 4,12C4,7.59 7.59,4 12,4C16.41,4 20,7.59 20,12C20,16.41 16.41,20 12,20M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2M11,17H13V11H11V17Z" />
    		</svg>
	    </a>
        <a class="sidemenuitem" href="/cards">Cards</a>
        <a class="sidemenuitem" href="/tabs">
			<svg style="width:44px;height:44px" viewBox="0 0 24 24">
      		<path fill="#000000" d="M12,11.5A2.5,2.5 0 0,1 9.5,9A2.5,2.5 0 0,1 12,6.5A2.5,2.5 0 0,1 14.5,9A2.5,2.5 0 0,1 12,11.5M12,2A7,7 0 0,0 5,9C5,14.25 12,22 12,22C12,22 19,14.25 19,9A7,7 0 0,0 12,2Z" />
    		</svg>
		</a>
        <a class="sidemenuitem" href="/table">
			<svg style="width:44px;height:44px" viewBox="0 0 24 24">
    		<path fill="#000000" d="M9,2A7,7 0 0,1 16,9C16,10.57 15.5,12 14.61,13.19L15.41,14H16L22,20L20,22L14,16V15.41L13.19,14.61C12,15.5 10.57,16 9,16A7,7 0 0,1 2,9A7,7 0 0,1 9,2M5,8V10H13V8H5Z" />
			</svg>
		</a>
		<a class="sidemenuitem" href="/">
			<svg style="width:16px;height:16px" viewBox="0 0 24 24">
				<path fill="#000000" d="M11,9H13V7H11M12,20C7.59,20 4,16.41 4,12C4,7.59 7.59,4 12,4C16.41,4 20,7.59 20,12C20,16.41 16.41,20 12,20M12,2A10,10 0 0,0 2,12A10,10 0 0,0 12,22A10,10 0 0,0 22,12A10,10 0 0,0 12,2M11,17H13V11H11V17Z" />
			</svg> Info
		</a>    </SideMenu>

<script>
    import { onMount } from 'svelte';

    import { Card, Container, SideMenu} from '../components/index.js';

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
