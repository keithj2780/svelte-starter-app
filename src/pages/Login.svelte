
<Modal>
    <Container>
        <!-- Modal Content -->
        <Form className="animate">
            <div class="row" style="width:1%; margin:auto;">                
                <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Avatar">
            </div>

            <FormField label="fname">
                <input type="text" id="fname" name="firstname" placeholder="Your username..">
            </FormField>
            <FormField label="Password">
                <input type="text" id="pw" name="pw" placeholder="Your password..">
            </FormField>        
            
            <div class="row">
                <label><input type="checkbox" checked="checked" name="remember"> Remember me</label>
                    <button type="submit" on:click|preventDefault="{handleSubmit}" >
                        {#if busy}
                        <i class="fa fa-refresh fa-spin"></i>
                        {/if}
                        Login
                    </button>&nbsp;
                    <button type="button" onclick="document.getElementById('id01').style.display='none'" class="cancelbtn">Cancel</button>
            </div>
            <div class="row">
                Forgot <a href="/">password?</a>
            </div>
        </Form>
    </Container>
</Modal>

<script>
    import { onMount } from 'svelte';

    import { Accordian, Checkbox, Container, Counter, DatePicker, 
        Form, FormField, Modal, Section, StarRating, ToggleButton
        } from "../components/index.js";

    let name = 'Svelte';
    let busy = false;

    onMount(() => {
        busy = false;
    });
    function handleSubmit (e) {
        e.preventDefault();
        console.log('Got submit');
        console.log(e);
        busy = true;
    }
</script>
    
<style>
    img {
            height:128px;
    }

</style>
