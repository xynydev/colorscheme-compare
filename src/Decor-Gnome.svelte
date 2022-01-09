<script>
	export let title;
</script>

<main>
   <div class="title">{title}</div> <div class="windowdecorbutton gnome-decor"></div> <br>
   <!-- <hr> -->
</main>

<style>
    .gnome-decor {
        color: #666;
        position: absolute;
        right: 10px;
    }
    .title {
		position: absolute;
        left: 50%;
		transform: translate(-50%);

        font-size: 13px;
        font-family: "Hack Nerd Font Mono";
    }

    /* hr {
        position: absolute;
        left: 50%;
		transform: translate(-50%);
        color: #333;
        border: solid #333 1px;
    } */
</style>