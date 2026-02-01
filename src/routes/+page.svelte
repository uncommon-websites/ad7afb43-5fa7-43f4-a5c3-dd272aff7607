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

		// Split body text into words
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
			transform: translateY(12px);
		}
		100% {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@keyframes backgroundPulse {
		0%, 100% {
			opacity: 0.03;
		}
		50% {
			opacity: 0.06;
		}
	}

	.word {
		display: inline-block;
		opacity: 0;
		animation: wordFadeIn 0.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
		margin-right: 0.28em;
	}

	.word:last-child {
		margin-right: 0;
	}

	.highlight-badge {
		display: inline-block;
		background: linear-gradient(135deg, #f8f8f8 0%, #f0f0f0 100%);
		padding: 0.25rem 0.625rem;
		border-radius: 6px;
		font-weight: 700;
		border: 1px solid rgba(0, 0, 0, 0.06);
		transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
	}

	.highlight-badge:hover {
		background: linear-gradient(135deg, #ffffff 0%, #f5f5f5 100%);
		border-color: rgba(0, 0, 0, 0.1);
		transform: translateY(-1px);
	}

	.link-badge {
		display: inline-block;
		background: linear-gradient(135deg, #fafafa 0%, #f4f4f4 100%);
		padding: 0.125rem 0.375rem;
		border-radius: 4px;
		transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
		border: 1px solid rgba(0, 0, 0, 0.04);
		text-decoration: none;
		color: inherit;
		position: relative;
	}

	.link-badge::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		height: 1px;
		background: rgba(0, 0, 0, 0.15);
		transform: scaleX(0);
		transition: transform 0.25s cubic-bezier(0.16, 1, 0.3, 1);
	}

	.link-badge:hover {
		background: linear-gradient(135deg, #ffffff 0%, #f8f8f8 100%);
		border-color: rgba(0, 0, 0, 0.08);
		transform: translateY(-1px);
	}

	.link-badge:hover::after {
		transform: scaleX(1);
	}

	.cta-link {
		display: inline-block;
		background: linear-gradient(135deg, #f7f7f7 0%, #f0f0f0 100%);
		padding: 0.25rem 0.5rem;
		border-radius: 6px;
		transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
		border: 1px solid rgba(0, 0, 0, 0.06);
		text-decoration: none;
		color: inherit;
		font-weight: 500;
	}

	.cta-link:hover {
		background: linear-gradient(135deg, #000000 0%, #1a1a1a 100%);
		color: #ffffff;
		border-color: rgba(0, 0, 0, 0.2);
		transform: translateY(-2px);
	}

	.cta-link:active {
		transform: translateY(0);
	}

	.background-gradient {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		pointer-events: none;
		z-index: 0;
	}

	.gradient-orb {
		position: absolute;
		border-radius: 50%;
		filter: blur(80px);
		animation: backgroundPulse 8s ease-in-out infinite;
	}

	.gradient-orb-1 {
		width: 600px;
		height: 600px;
		background: radial-gradient(circle, rgba(99, 102, 241, 0.08) 0%, transparent 70%);
		top: -200px;
		left: -100px;
		animation-delay: 0s;
	}

	.gradient-orb-2 {
		width: 500px;
		height: 500px;
		background: radial-gradient(circle, rgba(168, 85, 247, 0.06) 0%, transparent 70%);
		bottom: -150px;
		right: -50px;
		animation-delay: 2s;
	}
</style>

<div class="min-h-screen flex flex-col justify-center items-center p-6 sm:p-10 md:p-16 lg:p-20 font-sans text-[#000000] bg-white selection:bg-primary-100 relative overflow-hidden">
	<!-- Subtle animated background -->
	<div class="background-gradient">
		<div class="gradient-orb gradient-orb-1"></div>
		<div class="gradient-orb gradient-orb-2"></div>
	</div>

	<!-- Centered content -->
	<div class="flex flex-col justify-center max-w-[920px] w-full mx-auto text-left relative z-10">
		
		<!-- Headline -->
		<h1 class="text-2xl sm:text-3xl md:text-4xl lg:text-[2.75rem] leading-[1.15] tracking-[-0.03em] text-[#000000] mb-8 sm:mb-10 md:mb-12" style="font-family: 'Inter', sans-serif; font-weight: 700;">
			{#each headlineWords as word, i}
				{#if word === '2x'}
					<span class="word" style="animation-delay: {i * 0.05}s;">
						<span class="highlight-badge">2x zero to unicorn</span>
					</span>
				{:else if word === 'zero' || word === 'to' || word === 'unicorn'}
					<!-- Skip these as they're part of the badge -->
				{:else}
					<span class="word" style="animation-delay: {i * 0.05}s;">{word}</span>
				{/if}
			{/each}
		</h1>

		<!-- Body Text -->
		<div class="mb-8 sm:mb-10 text-lg sm:text-xl md:text-[1.375rem] lg:text-[1.5rem] leading-[1.65] text-[#1a1a1a] font-normal tracking-[-0.01em]">
			<p>
				{#each bodyWords as word, i}
					{#if word === 'Public.com,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://public.com" target="_blank" rel="noopener noreferrer" class="link-badge">Public.com</a>,
						</span>
					{:else if word === 'Erebor,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://erebor.so/" target="_blank" rel="noopener noreferrer" class="link-badge">Erebor</a>,
						</span>
					{:else if word === 'Knotel,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://knotel.com" target="_blank" rel="noopener noreferrer" class="link-badge">Knotel</a>,
						</span>
					{:else if word === 'OpenWeb,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://openweb.com" target="_blank" rel="noopener noreferrer" class="link-badge">OpenWeb</a>,
						</span>
					{:else if word === 'BlankStreet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://blankstreet.com" target="_blank" rel="noopener noreferrer" class="link-badge">BlankStreet</a>,
						</span>
					{:else if word === 'GovDash,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://govdash.com" target="_blank" rel="noopener noreferrer" class="link-badge">GovDash</a>,
						</span>
					{:else if word === 'Voyantis,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://voyantis.ai" target="_blank" rel="noopener noreferrer" class="link-badge">Voyantis</a>,
						</span>
					{:else if word === 'Syrup.Tech,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://syrup.tech" target="_blank" rel="noopener noreferrer" class="link-badge">Syrup.Tech</a>,
						</span>
					{:else if word === 'Synonym,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://synonym.bio" target="_blank" rel="noopener noreferrer" class="link-badge">Synonym</a>,
						</span>
					{:else if word === 'TerraOne,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://terraone.io" target="_blank" rel="noopener noreferrer" class="link-badge">TerraOne</a>,
						</span>
					{:else if word === 'Duet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.joinduet.com" target="_blank" rel="noopener noreferrer" class="link-badge">Duet</a>,
						</span>
					{:else if word === 'Cambrium,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://cambrium.com" target="_blank" rel="noopener noreferrer" class="link-badge">Cambrium</a>,
						</span>
					{:else if word === 'Mango,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://mangomicro.com" target="_blank" rel="noopener noreferrer" class="link-badge">Mango</a>,
						</span>
					{:else if word === 'Elvy,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.elvyenergy.com/en" target="_blank" rel="noopener noreferrer" class="link-badge">Elvy</a>,
						</span>
					{:else if word === 'Flagship,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://flagship.io" target="_blank" rel="noopener noreferrer" class="link-badge">Flagship</a>,
						</span>
					{:else if word === 'Aer,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.aercompliance.com/" target="_blank" rel="noopener noreferrer" class="link-badge">Aer</a>,
						</span>
					{:else if word === 'Mine,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://usemine.com/" target="_blank" rel="noopener noreferrer" class="link-badge">Mine</a>,
						</span>
					{:else if word === 'WeMoney,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://wemoney.com.au" target="_blank" rel="noopener noreferrer" class="link-badge">WeMoney</a>,
						</span>
					{:else if word === 'getquin,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.getquin.com/portfolio-tracker/" target="_blank" rel="noopener noreferrer" class="link-badge">getquin</a>,
						</span>
					{:else if word === 'Cased,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://cased.com" target="_blank" rel="noopener noreferrer" class="link-badge">Cased</a>,
						</span>
					{:else if word === 'Ledge,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.ledge.co/" target="_blank" rel="noopener noreferrer" class="link-badge">Ledge</a>,
						</span>
					{:else if word === 'Rex,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.rex.app/en" target="_blank" rel="noopener noreferrer" class="link-badge">Rex</a>,
						</span>
					{:else if word === 'Classet,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://classet.com" target="_blank" rel="noopener noreferrer" class="link-badge">Classet</a>,
						</span>
					{:else if word === 'Colbr,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://www.colbr.co/" target="_blank" rel="noopener noreferrer" class="link-badge">Colbr</a>,
						</span>
					{:else if word === 'Pazago,'}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">
							<a href="https://pazago.com" target="_blank" rel="noopener noreferrer" class="link-badge">Pazago</a>,
						</span>
					{:else}
						<span class="word" style="animation-delay: {(headlineWords.length + i) * 0.05}s;">{word}</span>
					{/if}
				{/each}
			</p>
		</div>

		<!-- CTA -->
		<p class="text-lg sm:text-xl md:text-[1.375rem] lg:text-[1.5rem] leading-[1.65] text-[#1a1a1a] font-normal tracking-[-0.01em]">
			{#each ctaWords as word, i}
				{#if word === 'LinkedIn'}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.05}s;">
						<a href="https://www.linkedin.com/in/ron-zori-9b718681/" target="_blank" rel="noopener noreferrer" class="cta-link">LinkedIn</a>
					</span>
				{:else if word === 'ron@zori.me.'}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.05}s;">
						<a href="mailto:ron@zori.me" class="cta-link">ron@zori.me</a>.
					</span>
				{:else}
					<span class="word" style="animation-delay: {(headlineWords.length + bodyWords.length + i) * 0.05}s;">{word}</span>
				{/if}
			{/each}
		</p>
	</div>
</div>

