
<Modal>
    <Container>
        <!-- Modal Content -->
        <Form className="animate">
            <div class="row">
                <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Avatar">
            </div>

            <div class="row">
                <div class="col-25">
                    <label for="fname">Username</label>
                </div>
                <div class="col-75">
                    <input type="text" id="fname" name="firstname" placeholder="Your username..">
                </div>
            </div>
            <div class="row">
                <div class="col-25">
                    <label for="lname">Password</label>
                </div>
                <div class="col-75">
                    <input type="text" id="pw" name="pw" placeholder="Your password..">
                </div>
            </div>
        
            <div class="row">
                <span>
                    <button type="submit">Login</button>&nbsp;
                    <label><input type="checkbox" checked="checked" name="remember"> Remember me</label>
                    <button type="button" onclick="document.getElementById('id01').style.display='none'" class="cancelbtn">Cancel</button>
                </span>
            </div>
            <div class="row">
                Forgot <a href="/">password?</a>
            </div>
        </Form>
    </Container>
</Modal>

<script>
    import { onMount } from 'svelte';

    import Container from '../components/Container.svelte';
    import Modal from '../components/Modal.svelte';
    import Form from '../components/Form.svelte';
    export let router = {};
    
    // Those contains useful information about current route status
    router.path; // /test
    router.route; // Route Object
    router.params; // /about/bill/123/kansas { who: 'bill', where: 'kansas' }

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
