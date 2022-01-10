<script>
    let today = new Date();

    const days = ["Sun","Mon","Tue","Wed","Thu","Fri","Sat"];
    let weekday = days[today.getDay()];

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
    <div class="macos-bar">
        <div class=""></div> <strong>Colorscheme Compare</strong> File &nbsp;&nbsp; Edit
        <div class="date">{weekday} {month} {today.getDate()}&nbsp;&nbsp;&nbsp;{today.getHours()}:{getMinutes()}</div>
    </div>
</main>

<style>
    .macos-bar {
        user-select: none;

        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

        background-color: #ffffff0f;

        box-sizing: border-box;

        height: 27px;
        width: 100%;

        position: absolute;
        top: 0;
        left: 0;

        display: flex;
        align-items: center;

        padding: 6px;

        padding-left: 50px;

        font-size: 13px;
        font-weight: 300;
    }
    .date {
        position: absolute;
        right: 10px;
    }
    strong {
        font-weight: 600;
        margin-right: 20px;
    }
    . {
        position: absolute;
        left: 20px;

        font-family: Hack Nerd Font Mono;
        font-size: 21px;
        transform: translateY(-1.5px);
    }
</style>