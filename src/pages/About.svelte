
<h1>About {name}!</h1>
<p>Route is {router.path}</p>
<p>Path is {router.route}</p>
<p>Params from URL are {JSON.stringify(router.params)} and the keys are specified in the router</p>
<Container>

    <Section>
        <h2>Range slider</h2>
        <RangeSlider value={range} min="21" max="129" on:change={(e)=>range=e.detail}/>
        {range} selected<br />
    </Section>  
    <Section>
        <h2>Simple Hover menu with no menu options</h2>
        <HoverMenu isInfo={true} on:hover={() =>{console.log('hov')}}/>
    </Section>  
    <Section>
        <h2>Simple Hover menu</h2>
        <HoverMenu items={menuItems} on:menu={(cmd)=>cmdFromHoverMenu=cmd.detail}/><br /><br /><br />
        Got {cmdFromHoverMenu} from HoverMenu
    </Section>  
    <Section>
            <h2>Two Line Hover menu</h2>
            <HoverMenu items={menuItems} isTwoLine=true on:menu={(cmd)=>cmdFromHoverMenu2=cmd.detail}/><br /><br /><br />
        Got {cmdFromHoverMenu2} from HoverMenu
    </Section>  
        
    <Section>
        <h2>Tag Buttons</h2>
        <TagButton 
            lefttext='UAT'
            leftfg='blue'
            leftbg='rgb(5,5,5)'
            righttext='Normal'
            rightbg='green'
            rightfg='rgb(55,255,55)'
            on:click="{((side)=> tagSideClicked=side.detail)}"}
        />
        <TagButton
            lefttext='Production'
            leftfg='blue'
            leftbg='rgb(5,5,5)'
            righttext='Alert'
            rightbg='red'
            rightfg='rgb(55,255,55)'
            closeable={false}
            on:click="{(()=> { toastText = 'Production Issue. Alert clicked'; toastBlank.showToastForMS(3000)})}"
        />
        <br />
        {#if tagSideClicked.length}
            {tagSideClicked} side clicked
        {/if}<br />
    </Section>

    <SideTab side="left">
        <StyledLink class="sidenavitem" href="/table" style='background-color:rgb(131, 132, 187); top:41px;' >Table</StyledLink>
        <StyledLink class="sidenavitem" href="/contact" style='background-color:rgb(146, 206, 146); top:101px;'>Contact</StyledLink>
        <StyledLink class="sidenavitem" href="/cards" style='background-color:rgb(212, 156, 200); top:161px;'>Cards</StyledLink>
        <StyledLink class="sidenavitem" href="/tabs" style='background-color:rgb(212, 151, 151); top:221px;' >Tabs</StyledLink>
        <StyledLink class="sidenavitem" href="/carousel" style='background-color:rgb(151, 208, 212); top:281px;' >Carousel</StyledLink>
    </SideTab>

    <SideTab side="right">
        <StyledLink class="sidenavitem" href="/table" style='background-color:rgb(131, 132, 187); top:41px;' >Table</StyledLink>
        <StyledLink class="sidenavitem" href="/contact" style='background-color:rgb(146, 206, 146); top:101px;'>Contact</StyledLink>
        <StyledLink class="sidenavitem" href="/cards" style='background-color:rgb(212, 156, 200); top:161px;'>Cards</StyledLink>
        <StyledLink class="sidenavitem" href="/tabs" style='background-color:rgb(212, 151, 151); top:221px;' >Tabs</StyledLink>
        <StyledLink class="sidenavitem" href="/carousel" style='background-color:rgb(151, 208, 212); top:281px;' >Carousel</StyledLink>
    </SideTab>
        
    <Section>
    <Box>
        <h3>{name} Box Demo for {router.params.who} of {router.params.where}.</h3>
        <p><em>(mouse over for shadow effect)</em></p>
        <p>{name} is a radical new approach to building user interfaces. Whereas traditional frameworks like React and Vue do the bulk of their work in the browser, {name} shifts that work into a compile step that happens when you build your app.</p>
        <p>Instead of using techniques like virtual DOM diffing, Svelte writes code that surgically updates the DOM when the state of your app changes.</p>
    </Box>
    </Section>

    <Section>
        <h2>Buttons with a Badge (with Toast invoked)</h2>
        <button on:click="{() => toast1.showToastForMS(700)}" class="badgeContainer"><span>Toast demo</span>
            <span><Badge style="background:rgb(68, 153, 223)">700ms</Badge></span>
        </button>
        <button on:click="{() => toast2.showToastForMS(3000)}"  class="badgeContainer">Another Toast demo
                <span><Badge style="color:blue">3s</Badge></span>
        </button>
    </Section>

    <Section>
        <h2>Closeable Chips</h2>
        <span>
            <Chip img="https://randomuser.me/api/portraits/thumb/men/44.jpg" alt="Home" on:close="{() => loader4.show()}" closeable={true}>Berts Chip</Chip>
            <Loader  bind:this={loader4} modal={true} timeout=3000/>
            <p>When closing this chip. a modal loader shows for 3 secs</p>
        </span>
        <Chip img="https://randomuser.me/api/portraits/thumb/women/44.jpg" alt="Home" closeable={false}>Bettys Chip</Chip>
    </Section>

    <Container>
        <h2>Tooltips on hover and click</h2>
        <div class="badgeContainer">
            <span><Badge on:click={() => console.log('badge clicked')}>Recommended</Badge></span>
            <Popup popuptext="Great hovering" tooltip=true>
                <Box>Tooltip Demo happens for 3 secs if you hover over this box</Box>
            </Popup>
        </div>
    </Container>

    <Container>
        <Box class="badgeContainer">
            <Popup popuptext="Thanks for the hover" tooltip=true>
                Tooltip Demo happens for 3 secs if you hover over this text
            </Popup>
        </Box>
    </Container>

    <Container>
        <Popup popuptext="Thanks for the click" ms=3000>Popup Demo happens for 3 secs if you click this text</Popup>
        <Section><button on:click={doShowCallout}>Click to show the callout again</button></Section>
    </Container>

    <Container>
            Stuff that needs more explaination 
            <Popup popuptext="The Spark plan allows outbound network requests only to Google-owned services. Inbound invocation requests are allowed within the quota. On the Blaze plan, Cloud Functions provides a perpetual free tier. The first 2,000,000 invocations, 400,000 GB-sec, 200,000 CPU-sec, and 5 GB of Internet egress traffic is provided for free each month. You are only charged on usage past this free allotment. Pricing is based on total number of invocations, and compute time. Compute time is variable based on the amount of memory and CPU provisioned for a function. Usage limits are also enforced through daily and 100s quotas. For more information, see Cloud Functions Pricing."
            ms=3000  tooltip=true style="font-size:12px; text-align:left;padding:6px;"><i class="fa fa-question-circle"></i></Popup>
            <Section><button on:click={doShowCallout}>Click to show the callout again</button></Section>
    </Container>
           
    <Section>
        <p>
            <button on:click={setTheme1}>Set Green Theme</button>
            To set the theme, change the CSS vars in global.css :root 
        </p>
        
    </Section>

    <Section><button on:click={toggleLoader}>Toggle Loaders</button>
        <span>
            <Loader bind:this={loader1} />
            <Loader bind:this={loader2} type="2" speed="2"/>
            <Loader bind:this={loader3} type="3" speed="3"/>
            <Loader bind:this={loader7} type="7"/>
        </span>
    </Section>

    <Section>
        <h2> Click to flip to the reverse side</h2>
        <Flipper bind:flipped={isFlipped}  sideAStyle="background-color:red" sideBStyle="background-color:blue">
            <div slot="sideA">
                <h2>Bettys chip is below</h2>
                <Chip img="https://randomuser.me/api/portraits/thumb/women/44.jpg" alt="Home" closeable={false}>Bettys Chip</Chip>
                <p>Betty has a red car</p>
            </div>
            <div slot="sideB">
                <h2>Geoffs chip is below</h2>
                <Chip img="https://randomuser.me/api/portraits/thumb/men/18.jpg" alt="Home" closeable={false}>Geoffs Chip</Chip>
                <p>Geoff has a blue dog</p>
            </div>
        </Flipper>
        {isFlipped?"Side A":"SideB"}
    </Section>

</Container>

<Toast id='toast-1' bind:this={toast1} >This is some toast</Toast>
<Toast id='toast-2' bind:this={toast2} ><Chip img="https://randomuser.me/api/portraits/thumb/men/79.jpg" alt="Home">Chippo</Chip></Toast>
<Toast id='toast-3' bind:this={toast3} >Thanks for closing the Callout<br/>You're a real pal.</Toast>
<Toast bind:this={toastBlank} text={toastText} />
<Callout bind:this={calloutComponent} on:close="{() => toast3.showToastForMS(3000)}" header="This is a callout">Maybe you should consider a callout when you next need to ask your users if they know about cookies</Callout>

<script>
    import {onMount, createEventDispatcher} from 'svelte';
	import { Link, navigateTo } from 'svero';

    import { Accordian, Box, Checkbox, Container, Counter, DatePicker, 
            Form, Section, StyledLink, Toast,Chip,Badge,Loader,Flipper,
            SideTab,TagButton,RangeSlider,HoverMenu,Popup,Callout
        } from "../components/index.js";

    
    export let router = {};
  
    // Those contains useful information about current route status
    router.path;
    router.route
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

    let name = 'Svelte';
    let toast1;
    let toast2;
    let toast3;
    let toastBlank;
    let toastText;

    let loader1;
    let loader2;
    let loader3;
    let loader4;
    let loader7;
    let bLoaderVisible=false;

    let isFlipped;
    let tagSideClicked = '';
    let cmdFromHoverMenu;
    let cmdFromHoverMenu2;
    let range = 110;

    let calloutComponent;

    let menuItems = [
        {name:'Upload ',        cmd:'upload',   line2:"Upload a file",          active:true,},
        {name:'Download ',      cmd:'download', line2:"Download a file",        active:false,},
        {name:'Save ',          cmd:'save',     line2:"Save a small file",      active:false,},
        {name:'New ',           cmd:'new',      line2:"New File",               active:true,},
        {name:'Toggle Info',    cmd:'toggleInfo',line2:"Info toggler here",     active:true,},
        {name:'Other Stuff',    cmd:'more',     line2:"Do other stuff",         active:true,},
    ];

    onMount(() => {
        loader1.hide();
        loader2.hide();
        loader3.hide();
        loader4.hide();
    });

	export function doShowCallout() {
		calloutComponent.show();
	}

    export function setTheme1(col) {
        let colBG = 'rgb(82, 171, 53)';
        let colText = 'rgb(10,150,21)';
        let colBody = 'rgb(170,225,158)';
        let items = document.getElementsByTagName("body");
        if (items[0]) {
            items[0].style.setProperty('--body-color', colBody);
            items[0].style.setProperty('--textcolor', colText);
            items[0].style.setProperty('--componentbgcolor', colBG);      //  these CSS vars are in global.css :root{}
        }
    }
    function toggleLoader() {
        bLoaderVisible = !bLoaderVisible;
        if (bLoaderVisible) {
            loader1.show();
            loader2.show();
            loader3.show();
            loader7.show();
        } else {
            loader1.hide();
            loader2.hide();
            loader3.hide();
            loader7.hide();
        }
    }

</script>

<style>
	h1 {
		color: brown;
	}
</style>
