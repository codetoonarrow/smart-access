<script>
    let src = './images/educate.png';

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
    body{
        overflow: hidden;
    }

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

    a {
        display: block;
        color: #FF3266;
        cursor: pointer;
        margin-top: 10vh;
    }
    
    .logo {
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
<body>
    

<img on:click={showIframe} class ="logo" src="./images/white.png" alt="Smart access logo">
<img {src} alt="Man educated about product">
<h1>Educate</h1>
<p>Assist at the point of activity with process knowledge and product information.</p>
<a  class="skip" on:click={showWelcomeScreen}>Skip Tour</a>
<p>Already a user?<a class="login" href="/"> Login</a></p>
</body>