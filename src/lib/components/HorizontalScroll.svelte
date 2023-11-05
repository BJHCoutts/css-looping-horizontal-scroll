<script lang='ts'>
	import { onMount } from "svelte";


	onMount( () => {

		const scroller = document.querySelector('.media-scroller')

		if (!window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
			addAnimation()
		}

		function addAnimation() {
			if (!scroller?.children) return
			scroller.setAttribute('data-animated', 'true')
			const scrollerElementsAsArray = Array.from(scroller.children)
			scrollerElementsAsArray.forEach( (el) => {
				const duplicateEl = el.cloneNode(true)
				duplicateEl.setAttribute('aria-hidden', true)
				scroller.appendChild(duplicateEl)
			})
		}
	})

</script>

<h1 style="text-align: center">Infinite Scroll Animation</h1>

<div class="scroller-container" data-speed="fast">
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

<style>

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

	ul {
		list-style: none;
	}

</style>