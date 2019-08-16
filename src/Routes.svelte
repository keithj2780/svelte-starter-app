<script>
	import { Router, Route, Link, navigateTo } from 'svero';

	import EmployeeTable from './pages/EmployeeTable.svelte';
	import EmployeeTabs from './pages/EmployeeTabs.svelte';
	import Login from './pages/Login.svelte';
	import EmployeeCards from './pages/EmployeeCards.svelte';
	import Images from './pages/Images.svelte';
	import TimelinePage from './pages/TimelinePage.svelte';
	import EmployeeTestimonials from './pages/EmployeeTestimonials.svelte';
	import Index from './pages/Index.svelte';
	import Contact from './pages/Contact.svelte';
	import About from './pages/About.svelte';

    //	just some JSON test data to populate components
	import {emps} from './TestData.js';
  

</script>

<Router>
    <Route fallback path="*" component={Index} />
    <Route path="/login" component={Login} />
    <Route path="/contact/:firstname/:lastname/:rating" component={Contact} />
    <Route path="/table">
        <EmployeeTable employees={emps}/>
    </Route>
    <Route path="/tabs">
        <EmployeeTabs employees={emps}/>
    </Route>
    <Route path="/about/:who/:where" component={About} />
    <Route path="/carousel" component={Images}/>
    <Route path="/cards">
            <EmployeeCards employees={emps}/>
    </Route>
    <Route path="/testimonials">
        <EmployeeTestimonials employees={emps}/>
    </Route>
    <Route path="/timeline" component={TimelinePage}/>
    <Route path="/" component={Index} exact/>
</Router>
