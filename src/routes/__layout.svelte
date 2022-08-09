<script lang='ts'>
	import '../app.css';
	import Footer from '$lib/components/Footer.svelte'
	import Head from '$lib/components/Head.svelte'
	import Kofi from '$lib/components/Kofi.svelte'
	import ShareButton from '$lib/components/ShareButton.svelte'
	import { themeChange } from 'theme-change'
	import { onMount } from 'svelte'
	import Darkmode from '$lib/components/Darkmode.svelte'

	onMount(() => {
		themeChange(false)
	})

	const url = 'https://svelte-duply.pickyzz.dev'
	const title = 'Svelte-duply'
	const description = 'Sveltekit Template'
	const imageUrl = `${url}/screenshot.png`
</script>

<Head {title} {description} {url} {imageUrl} />
<Kofi name="pickyzz" label="Buy me Coffee" />
<ShareButton {url} {title} />
<main>
	<Darkmode />
	<Footer />
	<slot />
</main>
