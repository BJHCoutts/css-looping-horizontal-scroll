<ul class="media-scroller">
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
	<li class='media-element'></li>
</ul>

<style>

	.media-scroller {
		display: grid;
		grid-auto-flow: column;
		grid-auto-columns: 15%;
		grid-column-gap: 50px;
		overflow-x: auto;
		overscroll-behavior-inline: contain;
	}

	.media-element {
		background-color: rgb(40, 40, 112);
		height: 200px;
		width: 100%;
	}

</style>