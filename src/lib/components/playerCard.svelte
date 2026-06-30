<script>
    export var name = "";
    export var nickname = "";
    export var lives = 3;
    export var placement = "";
    export var seasons = "";
    export var season = false;

    /**
	 * @param {number} lives
	 */
    function getPlayerColour(lives) {
        if (lives >= 4) {
            return "darkGreenLife"
        } else if (lives === 3) {
            return "greenLife"
        } else if (lives === 2) {
            return "yellowLife"
        } else if (lives == 1) {
            return "redLife"
        } else {
            return "noLives"
        }
    }
</script>

<a href="/players/{name}">
    <div class={"PlayerCard"}>
        <img
        src={`/players/${name}.png`}
        on:error={(e) => e.target.src = '/players/placeholder.png'}
        class={`h-36 mx-auto mt-5 mb-10 drop-shadow-[0_35px_35px_rgba(0,0,0,0.6)] ${season ? getPlayerColour(lives) : ""}`}
        width="150"
        alt={nickname}
        />
        <h2 class={`montserrat text-2xl ${season ? getPlayerColour(lives) : ""}`}>
        <strong>{nickname}</strong>
        </h2>
        <p style="color:white">{name}</p>
        <p style="color:white">{placement}</p>
        <p style="color:white">{seasons}</p>
    </div>
</a>

<style>
    h2 {
        margin-bottom: 3px
    }
    p {
        margin: 0
    }
</style>