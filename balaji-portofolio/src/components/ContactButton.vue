<template>
	<div class="contact-button">
		<a
			@click="scrollIntoSection"
			class="contact-link" id="contact-navigation">
			<div class="contact-div">
				<svg class="contact-svg" viewBox="0 0 512 487" fill="none" xmlns="http://www.w3.org/2000/svg">
					<g>
					<path fill-rule="evenodd" clip-rule="evenodd" d="M494.807 285.713C494.779 288.28 492.68 290.34 490.114 290.321H141.202C130.119 277.647 120.562 263.717 112.726 248.815L110.268 244.335C108.308 240.795 109.246 236.353 112.47 233.907L142.627 210.449C153.057 202.279 155.46 187.467 148.148 176.418L127.873 145.988V21.76C127.859 20.511 128.349 19.309 129.232 18.426C130.115 17.543 131.317 17.053 132.566 17.067H490.113C491.362 17.053 492.564 17.543 493.447 18.426C494.33 19.309 494.82 20.511 494.806 21.76V285.713H494.807ZM318.106 147.67L460.724 39.51C464.477 36.667 469.823 37.4 472.671 41.149C474.042 42.952 474.639 45.226 474.332 47.47C474.025 49.714 472.838 51.744 471.033 53.112L328.407 161.263C318.263 168.757 304.418 168.757 294.274 161.263L151.691 53.112C147.935 50.264 147.199 44.909 150.048 41.153C152.896 37.397 158.251 36.661 162.007 39.51L304.572 147.67C308.607 150.602 314.071 150.602 318.106 147.67ZM151.101 255.591L238.516 161.98C241.779 158.843 246.923 158.799 250.239 161.88C253.554 164.961 253.889 170.094 251.001 173.578L163.585 267.231C160.371 270.678 154.97 270.867 151.523 267.653C148.076 264.439 147.887 259.038 151.101 255.591ZM372.665 161.558C376.113 158.343 381.513 158.533 384.727 161.98L472.117 255.591C475.332 259.039 475.142 264.439 471.695 267.653C468.247 270.868 462.847 270.678 459.633 267.231L372.243 173.62C369.028 170.172 369.218 164.772 372.665 161.558Z" fill="white"/>
					<path d="M229.317 388.549L233.652 390.93C244.549 397.023 258.266 394.196 265.865 384.291L289.315 354.143C291.981 350.747 296.805 349.964 300.408 352.342L380.954 406.034C384.613 408.473 385.713 413.355 383.454 417.127L363.256 450.8C359.038 458.033 352.185 463.353 344.133 465.648C303.796 476.741 233.2 467.355 126.055 360.202C18.9099 253.049 9.55889 182.46 20.6259 142.157C22.9189 134.106 28.2359 127.254 35.4649 123.034L69.1379 102.827C72.9109 100.573 77.7899 101.672 80.2309 105.327L133.948 185.873C136.33 189.475 135.547 194.303 132.147 196.966L101.99 220.424C92.0869 228.021 89.2589 241.735 95.3509 252.629L97.7399 256.964L97.7551 256.992C106.285 272.637 116.903 292.11 155.545 330.743C194.199 369.388 213.664 380.008 229.302 388.541L229.317 388.549Z" fill="white"/>
					</g>
				</svg>
				<span class="contact-text">Contact</span>
			</div>
		</a>
	</div>
</template>

<script>
export default {
	methods: {
		scrollIntoSection(event)  {
			let eventTarget = event.currentTarget;
			this.removeSiblingsClickedStyles(eventTarget);
			let id = eventTarget.getAttribute('id');
			let navigationIndex = id.indexOf('-');
			id = id.slice(0, navigationIndex);
			let idDom = document.getElementById(id);
			idDom.scrollIntoView({block: "center", behavior: "smooth"});
		},
		removeSiblingsClickedStyles(eventTarget) {
			let prevActiveNode = eventTarget.closest('.navigations').querySelector('.link-active-style');
			if(prevActiveNode) {
				prevActiveNode.classList.remove('link-active-style');
				prevActiveNode.querySelectorAll('.svg-theme-background').forEach(node => {
					node.classList.remove('svg-theme-active');
				});
			}
		}
	}
}
</script>

<style scoped>
	.contact-button {
		padding: 1rem 0;
		width: 13.5rem;
	}
	.contact-link {
		text-decoration: none;
		cursor: pointer;
	}
	.contact-div {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		background-color:rgb(29, 161, 242);
		border-radius: 9999px;
		padding: 0.85rem;
		text-align: center;
	}
	.contact-div:hover {
		background-color: rgb(26, 145, 218);
		transition: 0.5s;
	}
	.contact-text {
		color: white;
		font-weight: bold;
		font-size: 1.1rem;
	}
	.contact-svg {
		width: 1.7rem;
		height: 1.7rem;
		display: none;
	}
	@media (max-width: 1050px) {
		.contact-text {
			display: none;
			padding: 0;
			font-size: 0;
		}
		.contact-button {
			width: fit-content;
		}
		.contact-div {
			padding: 0.7rem;
		}
		.contact-svg {
			display: block;
		}
	}
	@media (max-width: 520px) {
		.contact-div {
			padding: 0.5rem;
		}
		.contact-button {
			margin-left: 0;
			padding: 0;
		}
		.contact-svg {
			width: 1.5rem;
			height: 1.5rem;
		}
	}
</style>