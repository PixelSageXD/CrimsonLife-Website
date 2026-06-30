<script>
    export var teamName = "";
</script>

<div class="teamCard">
    <h1 class="text-3xl md:text-5xl lg:text-5xl pb-5 montserrat text-gray-200 text-center">{teamName}</h1>
    <div class="teamGrid">
        <slot></slot>
    </div>
</div>

<style>
    .teamCard {
        padding: 1rem;
	    border-radius: 1rem;
	    margin-bottom: 2rem;
	    margin-left: 8rem;
	    margin-right: 8rem;
        background-color: #3f0524;
        box-shadow: 0 0 30px rgba(63, 5, 36, 0.3)
    }
</style>
