<h1>Use elements double the track width sie and the loop will be smooth, ideally do one loop and then duplicate item in js. You can also group them to slide the whole thing over too if the element group equals the track width</h1>

<section class="media-scroller-container" data-animated='true'>
	<ul class="media-scroller">
		<li class='media-element'>1</li>
		<li class='media-element'>2</li>
		<li class='media-element'>3</li>
		<li class='media-element'>4</li>
		<li class='media-element'>5</li>
		<li class='media-element'>6</li>
		<li class='media-element'>7</li>
		<li class='media-element'>8</li>
		<li class='media-element'>9</li>
	</ul>
</section>

<style>

	h1 {
		text-wrap: balance;
		text-align: center;
	}
	.media-scroller-container {
		/* max-width: 600px; */
	}

	.media-scroller-container[data-animated="true"] {
		overflow: hidden;
		-webkit-mask: linear-gradient(
			90deg,
			transparent,
			white 20%,
			white 80%,
			transparent
		);
		mask: linear-gradient(90deg, transparent, white 20%, white 80%, transparent);
	}


	.media-scroller {
		--_spacing: 50px;
		display: grid;
		grid-auto-flow: column;
		grid-auto-columns: 15%;
		grid-column-gap: var(--_spacing);
		overflow-x: show;
		overscroll-behavior-inline: contain;

		scroll-snap-type: inline mandatory;
		scroll-padding-inline: var(--_spacing);

		animation: scroll 20s linear infinite;
		flex-wrap: nowrap;
		width: fit-content;
	}

	@keyframes scroll {
		to {
			transform: translateX(-100%);
		}
	}
	.media-element {
		background-color: rgb(40, 40, 112);
		height: 200px;
		width: 100%;
		scroll-snap-align: start;
	}

	ul {
		list-style: none;
	}

</style>