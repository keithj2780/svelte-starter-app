
<h1>Contact us please {firstname}!</h1>
<Container>
    <Form>
        <FormField label="Toggling">
            <ToggleButton label="" value={toggleValue} bind:checked={toggleValue}></ToggleButton>{toggleValue}
        </FormField>

        <FormField label="Hobbies">
            <Checkbox label="" value={cbValue} bind:checked={cbValue}></Checkbox>{cbValue}
        </FormField>    
    
        <FormField label="Interests">
            <Checkbox label="" value={cbValue2} bind:checked={cbValue2}></Checkbox>{cbValue2}
        </FormField>    
    
        <FormField label="First Name">
            <input type="text" bind:value={firstname} id="fname" name="firstname" value={firstname} placeholder="Your name..">
        </FormField>

        <FormField label="Last Name">
            <input type="text" bind:value={lastname} value={lastname} placeholder="Your last name..">
        </FormField>

        <FormField label="Password">
            <input type="password" bind:value={pw} value={pw} placeholder="An easy to guess password please..">
        </FormField>    

        <FormField label="Country">
            <select>
                <option value="au">Australia</option>
                <option value="ca">Canada</option>
                <option value="us">USA</option>
            </select>
        </FormField>

        <FormField label="Message">
            <textarea bind:value={message}  value={message} placeholder="Write something.." style="height:200px"></textarea>
        </FormField>

        <FormField label="How good is your day so far?">
            <span>
                <StarRating id="rating" bind:this={controlRating} bind:value={dayRating} bind:hoveredvalue={thinkingAboutRating}/>
                {#if thinkingAboutRating}
                    Thinking about a {thinkingAboutRating} rating ?
                {:else}
                    {dayRating} stars is {dayRating >= 4 ? "great" : (dayRating >= 2 ? "so-so" : "not so good.. huh?")}
                {/if}
                <br />
            </span>
        </FormField>
            
        <FormField label="Favorite Number?">
            <span><Counter bind:count={favNum} style="margin:6px"/> Have you considered {favNum*2} ?</span>
        </FormField>

        <FormField label="Pick a date">
            <input type="text" on:click={()=>show_date_picker=!show_date_picker} bind:value={picked_date} placeholder="Pick a date">
            {#if show_date_picker}
            <DatePicker
                format={"DD/MM/YYYY"}
                on:date={(event) => {picked_date = event.detail.date; picked_dateObj = event.detail.date_object; console.log(event.detail);}}
                on:cancel={() => show_date_picker = false}
            />
            {/if}
            {#if picked_dateObj}
                <p>Epoch Time is {picked_dateObj.getTime()}</p>
            {/if}
        </FormField>

        <div class="row">
            <Accordian header="Supplementary Info">
                <FormField label="Bonus Info goes here">
                    <textarea bind:value={message2}  value={message2} placeholder="Write something else .." style="height:200px"></textarea>
                </FormField>                
            </Accordian>
        </div>

        <div class="row">
            {#if busy}
            <button class="button" style="margin:12px" disabled><i class="fa fa-refresh fa-spin"></i> Submitting</button>
            <button class="button" style="margin:12px" disabled>Cancel</button>
            {:else}
            <button class="button" style="margin:12px" on:click={handleSubmit}>Submit</button>
            <button class="button" style="margin:12px" >Cancel</button>
            {/if}
        </div>
    </Form>
</Container>
    

<script>
    import { onMount } from 'svelte';

    import { Accordian, Checkbox, Container, Counter, DatePicker, 
        Form, FormField, Section, StarRating, ToggleButton
        } from "../components/index.js";

        export let router = {};
      
    // Those contains useful information about current route status
    router.path; // /test
    router.route; // Route Object
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

    $: {
        router.params;
        //console.log('router params='+JSON.stringify(router,null,2));
        initFields();
    }

    let toggleValue=false;
    let cbValue=false;
    let cbValue2=true;
    let firstname="";
    let lastname="";
    let pw="";
    let message="";
    let message2="";
    let dayRating=1;
    let thinkingAboutRating=0;
    let favNum=44;
    let picked_date = "05/08/2019";
    let picked_dateObj;
    let show_date_picker = false;

    let controlRating;

    let busy = false;
    
    $: console.log("cbValue changed to "+cbValue);
    $: console.log("cbValue2 changed to "+cbValue2);
    $: console.log("toggleValue changed to "+toggleValue);

    onMount(() => {
        busy = false;
        initFields();
    });
    function initFields() {
        if (router.params.firstname) firstname = router.params.firstname;
        if (router.params.lastname) lastname = router.params.lastname;
        if (router.params.rating) dayRating = router.params.rating;
        if (controlRating) controlRating.setValue(dayRating);
    }

    function handleSubmit (e) {
        e.preventDefault();
        console.log('Got submit');
        console.log(e);
        busy = true;
        console.log(firstname);
        console.log(lastname);
        console.log(message);
        console.log(dayRating);
    }
</script>
    
<style>
    h1 {
        color: rgb(94, 160, 185);
    }
</style>

    