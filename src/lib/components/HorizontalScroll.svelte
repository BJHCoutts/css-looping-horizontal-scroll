<script lang='ts'>

	import { onMount } from "svelte";

	onMount( () => {

		const scrollers = document.querySelectorAll(".scroller-container");

		// If a user hasn't opted in for recuded motion, then we add the animation
		if (!window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
			addAnimation();
		}

		function addAnimation() {
			scrollers.forEach((scroller) => {
				// add data-animated="true" to every `.scroller` on the page
				scroller.setAttribute("data-animated", "true");

				// Make an array from the elements within `.scroller-inner`
				const scrollerInner = scroller.querySelector(".scroller__inner");
				
				if (scrollerInner) {

					const scrollerContent = Array.from(scrollerInner.children);
	
					// For each item in the array, clone it
					// add aria-hidden to it
					// add it into the `.scroller-inner`

					scrollerContent.forEach((item) => {
						const duplicatedItem = item.cloneNode(true);
						duplicatedItem.setAttribute("aria-hidden", true);
						scrollerInner.appendChild(duplicatedItem);
					});
				}
			});
		}
	})

</script>

<section>

	<h1 style="text-align: center">Infinite Scroll Animation</h1>
	
	<div class="scroller-container" data-speed="fast" >
		<ul class="tag-list scroller__inner">
			<li>HTML</li>
			<li>CSS</li>
			<li>JS</li>
			<li>SSG</li>
			<li>webdev</li>
			<li>animation</li>
			<li>UI/UX</li>
		</ul>
	</div>
	
	<div class="scroller-container" data-direction="right" data-speed="slow">
		<div class="scroller__inner">
			<img src="https://i.pravatar.cc/150?img=1" alt="" />
			<img src="https://i.pravatar.cc/150?img=2" alt="" />
			<img src="https://i.pravatar.cc/150?img=3" alt="" />
			<img src="https://i.pravatar.cc/150?img=4" alt="" />
			<img src="https://i.pravatar.cc/150?img=5" alt="" />
			<img src="https://i.pravatar.cc/150?img=6" alt="" />
		</div>
	</div>

</section>

<!-- <a class="yt" href="https://youtu.be/pKHKQwAsZLI">
  Watch the tutorial
</a> -->

<style>

:root {
  --clr-neutral-100: hsl(0, 0%, 100%);
  --clr-primary-100: hsl(205, 15%, 58%);
  --clr-primary-400: hsl(215, 25%, 27%);
  --clr-primary-800: hsl(217, 33%, 17%);
  --clr-primary-900: hsl(218, 33%, 9%);
}

	section {
		color-scheme: dark;
		display: grid;
		min-block-size: 100vh;
		place-content: center;
		font-family: system-ui;
		font-size: 1.125rem;
		background-color: var(--clr-primary-800);
		color: var(--clr-neutral-100);
	}
	h1 {
		text-wrap: balance;
		text-align: center;
	}
	.scroller-container {
		max-width: 600px;
	}

	.scroller-container[data-animated="true"] {
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


	.scroller__inner {
		padding-block: 50px;
		display: flex;
		flex-wrap: wrap;
		gap: 25px;
		/* --_spacing: 50px;
		display: grid;
		grid-auto-flow: column;
		grid-auto-columns: 15%;
		grid-column-gap: var(--_spacing);
		overflow-x: show;
		overscroll-behavior-inline: contain;

		scroll-snap-type: inline mandatory;
		scroll-padding-inline: var(--_spacing);

		animation: scroll 5s linear infinite;
		flex-wrap: wrap; */
	}

	.scroller-container[data-animated="true"] .scroller__inner {
		width: max-content;
		flex-wrap: nowrap;
		animation: scroll var(--_animation-duration, 40s)
    var(--_animation-direction, forwards);
	}

	@keyframes scroll {
		to {
			transform: translateX(calc(-50%) - 0.5rem);
		}
	}

	.scroller[data-direction="right"] {
  --_animation-direction: reverse;
}

.scroller[data-direction="left"] {
  --_animation-direction: forwards;
}

.scroller[data-speed="fast"] {
  --_animation-duration: 20s;
}

.scroller[data-speed="slow"] {
  --_animation-duration: 60s;
}

	.media-element {
		background-color: rgb(40, 40, 112);
		height: 200px;
		width: 100%;
		scroll-snap-align: start;
	}

	.tag-list {
		list-style: none;
		padding-inline: 0;
		margin: 0;
	}

	.tag-list > li {
		padding: 1rem;
		background: var(--clr-primary-400);
		border-radius: 0.5rem;
		box-shadow: 0 0.5rem 1rem -0.25rem var(--clr-primary-900);
	}

</style>