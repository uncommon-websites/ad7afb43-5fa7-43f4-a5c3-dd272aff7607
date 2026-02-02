<script lang="ts">
	import "../app.css";
	import { onMount } from 'svelte';

	let headlineWords = $state<string[]>([]);
	let bodyWords = $state<string[]>([]);
	let ctaWords = $state<string[]>([]);

	onMount(() => {
		// Split headline into words, preserving the highlighted span
		const headlineText = "Ron is a venture investor and 2x zero to unicorn growth leader.";
		headlineWords = headlineText.split(' ');

		// Split body text into words, removing the <br> tag
		const bodyText = "He invested, advised or led growth for Public.com, Erebor, Knotel, OpenWeb, BlankStreet, GovDash, Voyantis, Syrup.Tech, Synonym, TerraOne, Duet, Cambrium, Mango, Elvy, Flagship, Aer, Mine, WeMoney, getquin, Cased, Ledge, Rex, Classet, Colbr, Pazago, played pro soccer in Israel and studied philosophy and economics at Columbia.";
		bodyWords = bodyText.split(' ');

		// Split CTA into words
		const ctaText = "DM anytime on LinkedIn or at ron@zori.me.";
		ctaWords = ctaText.split(' ');
	});
</script>

<style>
	@keyframes wordFadeIn {
		0% {
			opacity: 0;
			transform: translateY(10px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
		}
	}

	.word {
		display: inline-block;
		opacity: 0;
		animation: wordFadeIn 0.3s ease-out forwards;
		margin-right: 0.25em;
	}

	.word:last-child {
		margin-right: 0;
	}

	.highlight-badge {
		display: inline-block;
		background: #F3F4F6;
		padding: 2px 4px;
		border-radius: 4px;
		font-size: inherit;
		line-height: inherit;
		font-weight: inherit;
	}

	.link-badge {
		display: inline-block;
		background: #F3F4F6;
		padding: 2px 4px;
		border-radius: 4px;
		margin-right: -0.25em;
	}

	.cta-link {
		display: inline-block;
		background: #F3F4F6;
		padding: 2px 4px;
		border-radius: 4px;
		transition: background-color 0.2s;
	}

	.cta-link:hover {
		background: #e5e7eb;
	}
</style>

<div class="min-h-screen flex flex-col justify-center items-center p-6 sm:p-8 md:p-12 lg:p-16 font-sans text-[#000000] bg-white selection:bg-gray-200">
	<!-- Centered content -->
	<div class="flex flex-col justify-center max-w-[900px] mr-auto text-left">
		
		<!-- Headline -->
		<h1 class="tracking-[-0.02em] text-[#000000]" style="font-family: 'Inter', sans-serif; font-weight: 700; font-size: var(--text-xl); line-height: var(--text-xl--line-height);">
			{#each headlineWords as word, i}
				{#if word === '2x'}
					<span class="word" style="animation-delay: {i * 0.04}s;">
						<span class="highlight-badge">2x zero to unicorn</span>
					</span>
				{:else if word === 'zero' || word === 'to' || word === 'unicorn'}
					<!-- Skip these as they're part of the badge -->
				{:else}
					<span class="word" style="animation-delay: {i * 0.04}s;">{word}</span>
				{/if}
			{/each}
		</h1>

		<!-- Body Text -->
		<div class="my-6 text-[#6B7280] tracking-tight" style="font-family: 'Inter', sans-serif; font-weight: 700; font-size: var(--text-lg); line-height: 1.3;">
			<p>
				{#each bodyWords as word, i}
					{#if word === 'Public.com,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://public.com" target="_blank" rel="noopener noreferrer" class="link-badge">Public.com</a>,
						</span>
					{:else if word === 'Erebor,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://erebor.so/" target="_blank" rel="noopener noreferrer" class="link-badge">Erebor</a>,
						</span>
					{:else if word === 'Knotel,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://knotel.com" target="_blank" rel="noopener noreferrer" class="link-badge">Knotel</a>,
						</span>
					{:else if word === 'OpenWeb,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://openweb.com" target="_blank" rel="noopener noreferrer" class="link-badge">OpenWeb</a>,
						</span>
					{:else if word === 'BlankStreet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://blankstreet.com" target="_blank" rel="noopener noreferrer" class="link-badge">BlankStreet</a>,
						</span>
					{:else if word === 'GovDash,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://govdash.com" target="_blank" rel="noopener noreferrer" class="link-badge">GovDash</a>,
						</span>
					{:else if word === 'Voyantis,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://voyantis.ai" target="_blank" rel="noopener noreferrer" class="link-badge">Voyantis</a>,
						</span>
					{:else if word === 'Syrup.Tech,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://syrup.tech" target="_blank" rel="noopener noreferrer" class="link-badge">Syrup.Tech</a>,
						</span>
					{:else if word === 'Synonym,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://synonym.bio" target="_blank" rel="noopener noreferrer" class="link-badge">Synonym</a>,
						</span>
					{:else if word === 'TerraOne,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://terraone.io" target="_blank" rel="noopener noreferrer" class="link-badge">TerraOne</a>,
						</span>
					{:else if word === 'Duet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.joinduet.com" target="_blank" rel="noopener noreferrer" class="link-badge">Duet</a>,
						</span>
					{:else if word === 'Cambrium,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://cambrium.com" target="_blank" rel="noopener noreferrer" class="link-badge">Cambrium</a>,
						</span>
					{:else if word === 'Mango,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://mangomicro.com" target="_blank" rel="noopener noreferrer" class="link-badge">Mango</a>,
						</span>
					{:else if word === 'Elvy,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.elvyenergy.com/en" target="_blank" rel="noopener noreferrer" class="link-badge">Elvy</a>,
						</span>
					{:else if word === 'Flagship,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://flagship.io" target="_blank" rel="noopener noreferrer" class="link-badge">Flagship</a>,
						</span>
					{:else if word === 'Aer,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.aercompliance.com/" target="_blank" rel="noopener noreferrer" class="link-badge">Aer</a>,
						</span>
					{:else if word === 'Mine,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://usemine.com/" target="_blank" rel="noopener noreferrer" class="link-badge">Mine</a>,
						</span>
					{:else if word === 'WeMoney,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://wemoney.com.au" target="_blank" rel="noopener noreferrer" class="link-badge">WeMoney</a>,
						</span>
					{:else if word === 'getquin,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.getquin.com/portfolio-tracker/" target="_blank" rel="noopener noreferrer" class="link-badge">getquin</a>,
						</span>
					{:else if word === 'Cased,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://cased.com" target="_blank" rel="noopener noreferrer" class="link-badge">Cased</a>,
						</span>
					{:else if word === 'Ledge,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.ledge.co/" target="_blank" rel="noopener noreferrer" class="link-badge">Ledge</a>,
						</span>
					{:else if word === 'Rex,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.rex.app/en" target="_blank" rel="noopener noreferrer" class="link-badge">Rex</a>,
						</span>
					{:else if word === 'Classet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://classet.com" target="_blank" rel="noopener noreferrer" class="link-badge">Classet</a>,
						</span>
					{:else if word === 'Colbr,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://www.colbr.co/" target="_blank" rel="noopener noreferrer" class="link-badge">Colbr</a>,
						</span>
					{:else if word === 'Pazago,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">
							<a href="https://pazago.com" target="_blank" rel="noopener noreferrer" class="link-badge">Pazago</a>,
						</span>
					{:else if word.includes('and') && i > 0 && bodyWords[i - 1] === 'Israel'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">{word}</span>
						<br />
					{:else}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.04}s;">{word}</span>
					{/if}
				{/each}
			</p>
		</div>

		<!-- CTA -->
		<p class="text-[#6B7280] tracking-tight" style="font-family: 'Inter', sans-serif; font-weight: 700; font-size: var(--text-lg); line-height: 1.3;">
			{#each ctaWords as word, i}
				{#if word === 'LinkedIn'}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.04}s;">
						<a href="https://www.linkedin.com/in/ron-zori-9b718681/" target="_blank" rel="noopener noreferrer" class="cta-link">LinkedIn</a>
					</span>
				{:else if word === 'ron@zori.me.'}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.04}s;">
						<a href="mailto:ron@zori.me" class="cta-link">ron@zori.me</a>.
					</span>
				{:else}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.04}s;">{word}</span>
				{/if}
			{/each}
		</p>
	</div>
</div>

