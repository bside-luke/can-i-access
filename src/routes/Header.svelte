<header>
	<div class="corner">
		<a href="https://chainmonsters.com">
			<img
				class="icon"
				src="https://chainmonsters.com/_next/image?url=%2Fimages%2Fchipleaf_head.png&w=64&q=75"
				alt="SvelteKit"
			/>
		</a>
	</div>

	<div class="corner">
		<a href="https://github.com/bside-luke">
			<svg class="icon" viewBox="0 0 16 16" version="1.1" aria-hidden="true" width="24" height="24" xmlns="http://www.w3.org/2000/svg">
				<path
					fill="#FFFFFF"
					fill-rule="evenodd"
					clip-rule="evenodd"
					d="M8 0C3.58 0 0 3.582 0 8c0 3.535 2.303 6.533 5.5 7.59.4.074.547-.174.547-.387 0-.192-.007-.7-.01-1.374-2.238.485-2.707-1.084-2.707-1.084-.365-.927-.89-1.174-.89-1.174-.727-.498.055-.487.055-.487.805.057 1.232.83 1.232.83.718 1.234 1.884.877 2.34.668.072-.525.281-.877.51-1.078-1.785-.202-3.655-.894-3.655-3.973 0-.878.312-1.596.824-2.157-.083-.203-.36-1.018.079-2.121 0 0 .672-.215 2.2.82.638-.178 1.318-.267 2-.271.682.004 1.362.093 2 .27 1.527-1.035 2.198-.82 2.198-.82.44 1.103.163 1.918.08 2.12.514.561.825 1.28.825 2.157 0 3.086-1.874 3.767-3.665 3.965.288.248.545.736.545 1.483 0 1.071-.01 1.937-.01 2.198 0 .215.144.465.55.386A8.002 8.002 0 0 0 16 8c0-4.418-3.582-8-8-8z"
				/>
			</svg>
		</a>
	</div>
</header>

<style>
	.icon:hover {
		transform: scale(1.2);
		transition: transform 0.2s;
		transition-timing-function: cubic-bezier(0.5, 1.6, 0.4, 0.7);
	}

	header {
		background: linear-gradient(to bottom, #08333333 0%, #07333333 100%);
		width: 100%;
		display: flex;
		justify-content: space-between;
	}

	.corner {
		width: 3em;
		height: 3em;
	}

	.corner a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 100%;
	}

	.corner img {
		width: 2em;
		height: 2em;
		object-fit: contain;
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
