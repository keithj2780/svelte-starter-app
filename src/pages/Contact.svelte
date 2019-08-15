<script>
    import { onMount } from 'svelte';

    import Container from '../components/Container.svelte';
    import Section from '../components/Section.svelte';
    import Form from '../components/Form.svelte';
    import StarRating from '../components/StarRating.svelte';
    import DatePicker from "../components/DatePicker.svelte";
    import Counter from "../components/Counter.svelte";

    export let router = {};
      
    // Those contains useful information about current route status
    router.path; // /test
    router.route; // Route Object
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

    let firstname="";
    let lastname="";
    let message="";
    let dayRating=1;
    let thinkingAboutRating=0;
    let favNum=44;
    let picked_date = "05/08/2019";
    let show_date_picker = false;

    let controlRating;

    let busy = false;

    onMount(() => {
        busy = false;
        if (router.params.firstname) firstname = router.params.firstname;
        if (router.params.lastname) lastname = router.params.lastname;
        if (router.params.rating) dayRating = router.params.rating;
        controlRating.setValue(dayRating);
    });

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
    
    
    <h1>Contact us please {firstname}!</h1>
    <Container>
        <Form>
            <div class="row">
            <div class="col-25">
                <label for="fname">First Name</label>
            </div>
            <div class="col-75">
                <input type="text" bind:value={firstname} id="fname" name="firstname" value={firstname} placeholder="Your name..">
            </div>
            </div>
            <div class="row">
            <div class="col-25">
                <label for="lname">Last Name</label>
            </div>
            <div class="col-75">
                <input type="text" bind:value={lastname} value={lastname} placeholder="Your last name..">
            </div>
            </div>
            <div class="row">
            <div class="col-25">
                <label for="country">Country</label>
            </div>
            <div class="col-75">
                <select>
                <option value="australia">Australia</option>
                <option value="canada">Canada</option>
                <option value="usa">USA</option>
                </select>
            </div>
            </div>
            <div class="row">
            <div class="col-25">
                <label for="message">Message</label>
            </div>
            <div class="col-75">
                <textarea bind:value={message}  value={message} placeholder="Write something.." style="height:200px"></textarea>
            </div>
            </div>

            <div class="row">
                <div class="col-25">
                    <label for="rating">How good is your day so far?</label>
                </div>
                <div class="col-75">
                    <span>
                        <StarRating id="rating" bind:this={controlRating} bind:value={dayRating} bind:hoveredvalue={thinkingAboutRating}/>
                        {dayRating} stars is {dayRating >= 4 ? "great" : (dayRating >= 2 ? "so-so" : "not so good.. huh?")}
                        {#if thinkingAboutRating}<br />
                            Thinking about a {thinkingAboutRating} rating ?
                        {/if}
                        <br />
                    </span>
                </div>
            </div>

            <div class="row">
                <div class="col-25">
                    <label for="rating">Favorite Number?</label>
                </div>
                <div class="col-75">
                    <span><Counter bind:count={favNum} style="margin:6px"/> Have you considered {favNum*2} ?</span>
                </div>
            </div>

            <div class="row">
                <div class="col-25">
                    <label for="rating">Pick a date</label>
                </div>
                <div class="col-75">
                    <input type="text" on:click={()=>show_date_picker=true} bind:value={picked_date} placeholder="Pick a date">
                {#if show_date_picker}
                <DatePicker
                    format={"DD/MM/YYYY"}
                    on:date={(event) => picked_date = event.detail.date}
                    on:cancel={() => show_date_picker = false}
                />
                {/if}
                </div>
            </div>

            <div class="row">
                {#if busy}
                    <button class="button" disabled><i class="fa fa-refresh fa-spin"></i> Submitting</button>
                {:else}
                    <button class="button" on:click={handleSubmit}>Submit</button>
                {/if}
            </div>
        </Form>
        <Section></Section>
        <Section></Section>
        <Section></Section>
        <Section></Section>
    </Container>
    