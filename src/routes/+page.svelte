<script lang="ts">
	interface ContactInformation {
		phone: string;
		email: string;
		kvk: string;
	}

	let contactInformationShown = false;
	const showContactInformation = () => (contactInformationShown = true);

	function getContactInformation(): ContactInformation {
		const phonePart1 = '+3165';
		const phonePart2 = '3897779';
		const emailPart1 = 'baukew';
		const emailPart2 = 'estendorp@gmail.com';
		const kvkPart1 = '9463';
		const kvkPart2 = '3592';

		return {
			phone: phonePart1 + phonePart2,
			email: emailPart1 + emailPart2,
			kvk: kvkPart1 + kvkPart2
		};
	}
</script>

<svelte:head>
	<title>Home | Bauke Westendorp</title>
	<meta
		name="description"
		content="Op de homepagina van Bauke Westendorp uit Groningen
        lees je over zijn studies Communication & Multimedia Design en HBO-ICT.
        Hij kan zich onvoorwaardelijk vermaken
        met muziek, fotografie, video, kunst en programmeren.
        Ook vind je hier de contactinformatie voor makkelijk contact."
	/>
</svelte:head>

<div class="page">
	<section class="about">
		<enhanced:img
			src="$lib/img/bauke.jpg"
			alt="Een foto van Bauke Westendorp"
			class="bauke loading"
		/>
		<div>
			<h2>About</h2>

			<p>
				Hey, ik ben Bauke Westendorp! Sinds ik ben begonnen aan mijn studie
				<i>Communication &amp; Multimedia Design</i>
				aan de <i>Hanzehogeschool</i>
				(<a
					href="https://www.hanze.nl/nl/opleidingen/voltijd/bachelor/communication-and-multimedia-design"
					>"oh ja leuk zeg! En wat doe je bij die studie dan precies?"</a
				>) woon ik in mijn inmiddels favoriete stad Groningen. Ik kan me onvoorwaardelijk vermaken
				met muziek, fotografie, videografie, kunst en programmeren met een mespuntje sambal.
			</p>
			<br />
			<a href="/fotografie" class="button">Bekijk mijn werk</a>
		</div>
	</section>

	<section class="contact">
		<h2>Contact</h2>
		<p>Heb je vragen of wil je een samenwerking aangaan? Neem dan contact met mij op.</p>
		{#if contactInformationShown}
			<p>
				<b>Telefoon:</b>
				<a href={`tel:${getContactInformation().phone}`}>{getContactInformation().phone}</a>
				<br />
				<b>Email:</b>
				<a href={`mailto:${getContactInformation().email}`}>{getContactInformation().email}</a>
				<br />
				<b>KvK nummer:</b>
				{getContactInformation().kvk} (Westendorp AV)
			</p>
		{:else}
			<button on:click={showContactInformation}>Toon contactinformatie</button>
		{/if}
	</section>
</div>

<style>
	:global(main, header, footer) {
		padding-left: 2rem !important;
		padding-right: 2rem !important;
	}

	.page {
		display: flex;
		flex-direction: column;
	}

	.about {
		display: flex;
		align-items: center;
		gap: 2rem;
		margin-bottom: 2rem;
	}

	.about h2 {
		margin-bottom: 1rem;
	}

	.bauke {
		width: 24rem;
		height: 24rem;
		border-radius: 50%;
	}

	.contact {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	.contact button {
		align-self: flex-start;
	}

	@media (max-width: 800px) {
		.about {
			flex-direction: column;
			align-items: flex-start;
			gap: 1rem;
		}

		.bauke {
			width: 100%;
			height: 100%;
			max-width: 24rem;
		}
	}
</style>
