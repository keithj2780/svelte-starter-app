<Container>
    <h1>Employee Testimonials</h1>
    <p>We have loads of great tetimonials about our of Employees.</p>
    {#each employees as emp, i}
        <Testimonial alt={emp.fname+" "+emp.sname} img={emp.photo} style=width:400px>
        <h4>{emp.fname} - {emp.jobtitle}</h4>
        Great testimonial about employee {i} from {emp.city} who we know as {emp.fname} {emp.sname} 
        <br /><strong><i class="fa fa-envelope"></i></strong> : {emp.email}
        <br /><strong>DoB</strong>:{emp.dob.slice(0,10)} 
        </Testimonial>
        <br />
    {/each}
</Container>
        
<script>
    import { onMount } from 'svelte';

    import { Testimonial,Container} from '../components/index.js';

    export let employees;
    
    onMount(() => {
    });
    
    </script>
        
<style>

</style>
