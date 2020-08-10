<script>
    let src = './images/empower.png';

    import { createEventDispatcher } from 'svelte';
    
    const dispatchForWelcomeScreen = createEventDispatcher();
    function showWelcomeScreen() {
		dispatchForWelcomeScreen('welcome');
    }

    const dispatchForIframe = createEventDispatcher();
    function showIframe() {
		dispatchForIframe('website');
    }
    
</script>

<style>

    h1{
        color: #FFFFFF;
    }

    p{
        color: #FFFFFF;
        display:block;
        margin-left: 50px;
        margin-right: 50px;
    }
    
    img{
        display: block;
        margin: 0 auto;
        margin-top: 10vh;
    }

    button{
        background-color: #FF3266;
        color: #FFFFFF;
        border-radius: 10px;
        width: 60%;
        border: none;
        cursor: pointer;
    }

    a {
        display: block;
        color: #FF3266;
        cursor: pointer;
        margin-top: 10vh;
    }

    .logo{
        margin-top: 5vh;
        height: 2.5em;
        cursor: pointer;
    }

    .login{
        display: block;
        padding-left: 5px;
        color: #FF3266;
        display: inline;
    }

</style>

<div>

    <img on:click={showIframe} class='logo' src="./images/white.png" alt="Smart access logo">
    <img {src} alt="Person empowered about product">
    <h1>Empower</h1>
    <p>Enable your workforce to excel at their responsibilites, and provide exceptional customer service.</p>
    <button on:click={showWelcomeScreen}>Finish</button>
    <a on:click={showWelcomeScreen}>Skip Tour</a>
    <p>Already a user?<a class="login" href="">Login</a></p>

</div>


