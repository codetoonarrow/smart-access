<script>
	import Educate from './components/educate/educate.component.svelte';
	import Assess from './components/assess/assess.component.svelte';
	import Empower from './components/empower/empower.component.svelte';
	import Reader from './components/nfc-reader/nfc-reader.component.svelte';
	import Website from './components/logo/logo.component.svelte';

	const initializeSwiper = () => {
		md =  new Swiper('#swiper1',
		);
	}

	let showIframe = false;
	function handleSwitchToIframe(event) {
		showIframe = !showIframe
	} 

	let showModal = false;
	function handleSwitchToModal(event) {
		showModal = !showModal
	} 

	let visable = false;
	function handleSwitchToWelcomeScreen(event) {
		visable = !visable
	}

</script>

<style>

	main {
		text-align: center;
		padding: 1em;
		max-width: none;
		margin: 0 auto;
		padding: 0;
		height: 100%;
		background-color: #060A1B;
	}

html,
body,
.swiper-wrapper {
    padding: 0;
    margin: 0;
    width: 100%;
    height: 100%;
}

.swiper-slide {
    width: 100%;
    height: 100%;
}
.swiper-container {
    height: 100%;
}
</style>

<!-- Load in tiny-swiper js library -->
<svelte:head >
	<script src="https://unpkg.com/tiny-swiper@^1.0.0" ></script>
</svelte:head>
<svelte:window on:load={initializeSwiper} on:resize|passive={initializeSwiper}/>
	<main>
		<!-- Show iframe if the showIframe value true -->
		{#if showIframe}
			<Website />
		{/if}
		<!-- Show the tiny-swiper with each of onboarding components -->
		{#if !visable}
		<div class="foreground">
			<div class="swiper-container" id="swiper1">
				<div class="swiper-wrapper">
					<div class="a swiper-slide"><Educate on:website={handleSwitchToIframe} on:welcome={handleSwitchToWelcomeScreen}/></div>
					<div class="b swiper-slide"><Assess  on:website={handleSwitchToIframe} on:welcome={handleSwitchToWelcomeScreen} /></div>
					<div class="a swiper-slide" ><Empower on:website={handleSwitchToIframe} on:welcome={handleSwitchToWelcomeScreen}/></div>
				</div>
			</div>
		</div>
		{/if}
		<!-- Show the welcome screen -->
		<Reader on:modal={handleSwitchToModal} on:website={handleSwitchToIframe} {visable}/>	
	</main>



