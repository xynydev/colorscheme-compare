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
    <div class="gnome-bar">
        <div class="activities">Activities</div>
        <div class="date">{month} {today.getDate()}&nbsp;&nbsp;{today.getHours()}:{getMinutes()}</div>
        <div class="buttons"><div class="nf">墳 ⏻</div></div>
    </div>
</main>

<style>
    .gnome-bar {
        user-select: none;

        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

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
    .activities {
        position: absolute;
        left: 0px;
        border-radius: 20px;
        padding: 5px;
        padding-left: 20px;
        padding-right: 20px;

        transition: 100ms;
    }
    .date {
        position: absolute;
        left: 50%;
        transform: translate(-50%);
        border-radius: 20px;
        padding: 5px;
        padding-left: 10px;
        padding-right: 10px;

        transition: 100ms;
    }
    .buttons {
        position: absolute;
        right: 0px;
        padding-left: 20px;
        padding-right: 20px;
        font-weight: bold;
        word-spacing: 10px;

        border-radius: 20px;

        transition: 100ms;
    }
    .buttons .nf {
        transform: translateY(1.5px);
    }

    .activities:hover, .date:hover, .buttons:hover {
        background-color: #FFFFFF1F;
    }
</style>