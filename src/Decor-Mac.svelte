<script>
	export let title;
</script>

<main>
	<div class="title">{title}</div> <div class="windowdecorbutton mac-close"></div> <div class="windowdecorbutton mac-minize"></div> <div class="windowdecorbutton mac-maximize"></div>
</main>

<style>
    .mac-close {
		color: #FF625B;
	}

	.mac-minize {
		color: #FFBC2F;
	}

	.mac-maximize {
		color: #28CE42;
	}

	.title {
		position: absolute;
        left: 50%;
		transform: translate(-50%);

        font-size: 13px;
        font-family: "Hack Nerd Font Mono";
    }
</style>