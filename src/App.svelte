<script>
	// import Select from 'svelte-select';

	let selectedColorscheme;
	let colorschemes = ['Horizon Dark','Tokyo Night', 'Catpuccin'];

	let selectedWindowStyle;
	let windowstyles = ['WM', 'Gnome', 'Mac'];

	import * as horizondark from './themes/horizon-dark.json';
	import * as tokyonight from './themes/tokyo-night.json';
	import * as catpuccin from './themes/catpuccin.json';

	import Colorbars from './Colorscript-Colorbars.svelte';
	import Colorsquare from './Colorscript-Square.svelte';
	import SourceCodeExample from './SourceCodeExample.svelte';
	import WindowDecorMac from './Decor-Mac.svelte';
	import WindowDecorGnome from './Decor-Gnome.svelte';
	import BarMac from './Bar-Mac.svelte';
	import BarGnome from './Bar-Gnome.svelte';
	import BarWM from './Bar-WM.svelte';
	
	$: cssVarStyles = Object.entries(horizondark["default"])
		.map(([key, value]) => `--${key}:${value}`)
		.join(';');

	function changeColorscheme() {
		if (selectedColorscheme == 'Tokyo Night') {
			cssVarStyles = Object.entries(tokyonight["default"])
				.map(([key, value]) => `--${key}:${value}`)
				.join(';');
		} else if (selectedColorscheme == 'Catpuccin') {
			cssVarStyles = Object.entries(catpuccin["default"])
				.map(([key, value]) => `--${key}:${value}`)
				.join(';');
		} else if (selectedColorscheme == 'Horizon Dark') {
			cssVarStyles = Object.entries(horizondark["default"])
				.map(([key, value]) => `--${key}:${value}`)
				.join(';');
		}
	}

</script>

<main style={cssVarStyles}>	
	{#if selectedWindowStyle == 'Mac'}
		<BarMac/>
	{/if}
	{#if selectedWindowStyle == 'Gnome'}
		<BarGnome/>
	{/if}
	{#if selectedWindowStyle == 'WM'}
		<BarWM/>
	{/if}
	<div class="themeSelectArea">
		<div class="singleSelectArea">
			<h4>Colorscheme</h4>
			<select class="{selectedWindowStyle}" bind:value={selectedColorscheme} on:change="{() => changeColorscheme()}">
				{#each colorschemes as colorscheme}
				<option value={colorscheme}>
					{colorscheme}
				</option>
				{/each}
			</select>
		</div>
		<div class="singleSelectArea">
			<h4>Window style</h4>
			<select class="{selectedWindowStyle}" bind:value={selectedWindowStyle}>
				{#each windowstyles as windowstyle}
				<option value={windowstyle}>
					{windowstyle}
				</option>
				{/each}
			</select>
		</div>
	</div>

	<div class="terminal {selectedWindowStyle}">
		<div class="windowdecor">
			{#if selectedWindowStyle == 'Mac'}
				<WindowDecorMac title="bash-5.1"/>
			{/if}
			{#if selectedWindowStyle == 'Gnome'}
				<WindowDecorGnome title="bash-5.1"/>
			{/if}
		</div><br>
		[user@localhost] ~ # colorscript -r<br><br>
		<Colorsquare/>
	</div>

	<div class="terminal {selectedWindowStyle}">
		<div class="windowdecor">
			{#if selectedWindowStyle == 'Mac'}
				<WindowDecorMac title="bash-5.1"/>
			{/if}
			{#if selectedWindowStyle == 'Gnome'}
				<WindowDecorGnome title="bash-5.1"/>
			{/if}
		</div><br>
		[user@localhost] ~ # colorscript -r<br><br>
		<Colorbars/>
	</div>

	<div class="editor {selectedWindowStyle}">
		<div class="windowdecor">
			{#if selectedWindowStyle == 'Mac'}
				<WindowDecorMac title="vim"/>
			{/if}
			{#if selectedWindowStyle == 'Gnome'}
				<WindowDecorGnome title="vim"/>
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
		color: var(--term-normal-white);
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

	.Mac {
		box-shadow: #00000050 0px 10px 50px;
		border-radius: 6px;
		border: solid #333 1px;
	}

	.windowdecor {
		position: relative;
		padding: 0px;
	}

	.WM {
		border: solid var(--term-normal-black) 2px;
	}

	.WM:hover {
		border: solid var(--term-normal-magenta) 2px;
	}

	.Gnome {
		border-radius: 6px 6px 0px 0px;
		border: solid #333 1px;
	}

	:global(.windowdecorbutton) {
		display: inline;
		font-size: 20px;
	}

	.themeSelectArea {
		margin-top: 30px;
		margin-bottom: 20px;
		margin-left: 10px;
		line-height: 0px;

		display: flex;
		flex-direction: row;
	}

	.singleSelectArea {
		margin: 5px;
	}

	select {
		background-color: var(--term-normal-white);
		padding: 5px;
		width: 200px;
	}

	h1 {
		margin-top: 0;
		color: var(--term-normal-cyan);
	}
</style>