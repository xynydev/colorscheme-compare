<script>
    let today = new Date();

    const months = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sept","Oct","Nov","Dec"];
    let month = months[today.getMonth()];

    function getMinutes() {
        let minutes = today.getMinutes();
        if (minutes < 10) {
            return '0'+minutes
        }
        return minutes;
    }
</script>

<main>
    <div class="wm-bar">
        <div class="workspaces">[1]</div>
        <div class="title">[Colorscheme Compare]</div>
        <div class="date">[{month} {today.getDate()} {today.getHours()}:{getMinutes()}]</div>
    </div>
</main>

<style>
    .wm-bar {
        user-select: none;

        font-family: Hack Nerd Font Mono;

        box-sizing: border-box;

        height: 27px;
        width: 100%;

        position: absolute;
        top: 0;
        left: 0;

        display: flex;
        align-items: center;

        font-size: 13px;
        font-weight: 500;
    }
    .workspaces {
        position: absolute;
        left: 10px;
    }
    .title {
        position: absolute;
        left: 50%;
        transform: translate(-50%);
        border-radius: 20px;
        padding: 5px;
        padding-left: 10px;
        padding-right: 10px;

        transition: 100ms;
    }
    .date {
        position: absolute;
        right: 10px;
    }
</style>