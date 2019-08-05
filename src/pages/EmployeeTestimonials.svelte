<script>
    import { onMount } from 'svelte';
    import Testimonial from '../components/Testimonial.svelte';
    import Container from '../components/Container.svelte';

    export let router = {};
        
    // Those contains useful information about current route status
    router.path; // /test
    router.route; // Route Object
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

    export let employees;
    let empId=0;
    
    onMount(() => {
    });
    
    </script>
        
<style>
    h1 {
        color: grey;
    }

</style>

<Container>
    <h1>Employee Testimonials</h1>
    <p>We have loads of great tetimonials about our of Employees.</p>
    {#each employees as emp, i}
        <Testimonial alt={emp.name.first+" "+emp.name.last} img={emp.picture.large} style=width:400px>
        Great testimonial about employee {i} from {emp.location.timezone.description} who we know as {emp.name.first} {emp.name.last} 
        <br /><strong><i class="fa fa-envelope"></i></strong> : {emp.email}
        <br /><strong>DoB</strong>:{emp.dob.date.slice(0,10)} 
        </Testimonial>
        <br />
    {/each}
</Container>
        