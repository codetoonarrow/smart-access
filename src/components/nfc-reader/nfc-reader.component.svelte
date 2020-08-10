<script>
    import { fade } from 'svelte/transition';
    import { fly } from 'svelte/transition';
    import { createEventDispatcher } from 'svelte';

    export let visable = false;
    export const showWelcomeScreen = () => {
		visable = !visable
    }
    
    let src = './images/nfc reader.png';
    let showReader = false;


    const dispatchForIframe = createEventDispatcher();
    function showIframe() {
		dispatchForIframe('website');
    }

</script>

<style>

    img{
        display: block;
        margin: 0 auto;
        margin-top: 10vh;
    }
    .logo{
        margin-top: 5vh;
        height: 2.5em;
        cursor: pointer;
    }
    button{
        background-color: #FF3266;
        color: #FFFFFF;
        border-radius: 10px;
        width: 60%;
        border: none;
        cursor: pointer;
    }
    
    .backdrop{
        width:100%;
        height:100%;
        display: block;
        position: absolute;
        background: #F8F8F8;

        
    }
    .NFC-Reader{
        border-radius: 40px;
        z-index: 1000;
        width: 100%;
        height: 100%;
        top: 53vh;
        left: auto 0;
        position: fixed;
        background-color: grey;
        color: black;

    }
    .NFC-logo{
        
    }

    .login{
        display: block;
        padding-left: 5px;
        color: #FF3266;
        display: inline;
    }

</style>

{#if visable}
    <body>
        <div transition:fade class="backdrop">
            <img on:click={showIframe} class="logo" src="./images/color.png" alt="Smart Access Logo">
            <img src='./images/nfc reader.png' alt="NFC Reader app">
            <h1>Enable NFC Reader</h1>
            <p>Open the NFC reader on your iPhone to read the tag</p>
            <button on:click={() => showReader = !showReader}>Open Reader</button>
            <p>Already a user?<a class="login" href="/">Login</a></p>

            {#if showReader}
            
                <div class="NFC-Reader" transition:fly>
                    <h1>Ready to Scan</h1>
                    <img class='NFC-logo' src="./images/Group 97.png" alt="">
                    <p>Hold your device near the tag to scan it</p>
                    <button on:click={() => showReader = !showReader}>Cancel</button>
                </div>
            {/if}
        </div>
    </body>
{/if}



