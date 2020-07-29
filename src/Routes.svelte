<script>
    import Router from 'svelte-spa-router'

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

  
const routes = {
    // Exact path
    '/': Index,
    '/login':                                Login,
    "/contact/:firstname/:lastname/:rating": Contact,
    "/contact/:firstname/:lastname":         Contact,
    "/contact":         Contact,
    "/table":           EmployeeTable,    //   employees={emps}/>
    "/tabs":            EmployeeTabs,      //   employees={emps}/>
    "/about/:who/:where": About,
    "/about":           About,
    "/carousel":        Images,
    "/cards":           EmployeeCards,     //   employees={emps}/>
    "/testimonials":    EmployeeTestimonials,  //   employees={emps}/>
    "/timeline":        TimelinePage,
    // Catch-all
    // This is optional, but if present it must be the last
    '*': Index,
};

</script>
<Router {routes}/>

<!-- <Router>
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
</Router> -->
