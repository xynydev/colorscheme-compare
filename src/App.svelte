<script>
	import * as style from './themes/horizon-dark.json';

	import Colorbars from './Colorscript-Colorbars.svelte';
	import Colorsquare from './Colorscript-Square.svelte';
	import WindowDecorMac from './Decor-Mac.svelte';
	import SourceCodeExample from './SourceCodeExample.svelte';

	let windowStyle = 'mac';
	
	$: cssVarStyles = Object.entries(style["default"])
		.map(([key, value]) => `--${key}:${value}`)
		.join(';');

	console.log(style);
</script>

<main style={cssVarStyles}>
	<h1>Colorscheme Compare</h1>

	<div class="terminal {windowStyle}">
		<div class="windowdecor">
			{#if windowStyle == 'mac'}
				<WindowDecorMac/>
			{/if}
		</div><br>
		[user@localhost] ~ # colorscript -r<br><br>
		<Colorsquare/>
	</div>

	<div class="terminal {windowStyle}">
		<div class="windowdecor">
			{#if windowStyle == 'mac'}
				<WindowDecorMac/>
			{/if}
		</div><br>
		[user@localhost] ~ # colorscript -r<br><br>
		<Colorbars/>
	</div>

	<div class="editor {windowStyle}">
		<div class="windowdecor">
			{#if windowStyle == 'mac'}
				<WindowDecorMac/>
			{/if}
		</div>
		<SourceCodeExample/>
	</div>
</main>

<style>
	main {
		font-family: "Hack Nerd Font Mono";
		margin: 0;
		padding: 20px;
		box-sizing: border-box;
		background-color: var(--ui-background);
	}

	.terminal {
		font-family: "Hack Nerd Font Mono";
		font-size: 17px;
		color: var(--term-normal-white);
		padding: 10px;
		margin: 10px;
	}

	.editor {
		font-family: "Hack Nerd Font Mono";
		font-size: 14px;
		color: var(--term-normal-white);
		padding: 10px;
		margin: 10px;
	}

	.mac {
		box-shadow: #00000050 0px 10px 50px;
		border-radius: 6px;
		border: solid #333 1px;
	}

	:global(.windowdecorbutton) {
		display: inline;
		font-size: 20px;
	}

	h1 {
		margin-top: 0;
		color: var(--term-normal-cyan);
	}
</style>